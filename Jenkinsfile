nodeMaven{
    stage("Getting code"){
        checkout scm 
    }
    stage("Unit tests"){
        sh "mvn test"
    }
    stage("Compiling"){
        sh "mvn package -DskipTests"
    }
    stash includes: "target/*.jar", name: "artifact"
}
nodeKube{
    unstash "artifact"
    stage("Publishing app"){
        sh "kubectl -version"
    }
}