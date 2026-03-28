pipeline {
    agent any
    parameters{
        string(name: "NAME", defaultValue: "World", description: "Your name")
    }
    stages {
        stage('Hello') {
            steps {
                echo "Hello ${params.NAME}!"
            }
        }
    }
}
