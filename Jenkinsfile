pipeline {
    agent any  // Runs on any available Jenkins agent

    tools {
        jdk 'JDK17'  // Make sure JDK 17 is installed in Jenkins
        maven 'Maven' // Make sure Maven is installed in Jenkins
    }

    environment {
        JAVA_HOME = tool('JDK17')  // Set JAVA_HOME
        MAVEN_HOME = tool('Maven') // Set Maven path
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/3ncinasv3/spmLab3_valador.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn -B package --file pom.xml'  // Same as GitHub Actions
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'  // Runs tests with Maven
            }
        }

        stage('Custom Action') {
            steps {
                echo "Hello World"
            }
        }
    }

    post {
        success {
            echo 'Build and tests completed successfully! 🎉'
        }
        failure {
            echo 'Build or tests failed. Check the logs. ❌'
        }
    }
}
