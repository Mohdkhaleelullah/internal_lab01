//-------------------------------------------------------------------------------------------------------
pipeline {
    agent any
    tools{
        jdk 'JAVA_HOME'
        maven 'MAVEN_HOME'
    }
    stages {
        stage('git repo & clean') {
            steps {
                bat "rmdir /s /q Harshitha_Jenkins_Maven || exit 0"
                bat "git clone https://github.com/Harshitha-Macha/Harshitha_Jenkins_Maven.git"
                bat "mvn clean -f Harshitha_Jenkins_Maven/pom.xml"
            }
        }
        stage('install') {
            steps {
                bat "mvn install -f Harshitha_Jenkins_Maven/pom.xml" 
            }
        }
        stage('test') {
            steps {
                bat "mvn test -f Harshitha_Jenkins_Maven/pom.xml"
            }
        }
        stage('package') {
            steps {
                bat "mvn package -f Harshitha_Jenkins_Maven/pom.xml"
            }
        }

//-------------------------------------------------------------------------------------------------------


pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
    }

    stages {

        stage('Checkout from GitHub') {
            steps {
                echo "Cloning repository..."
                deleteDir()
                git url: 'https://github.com/', branch: 'main'
            }
        }

        stage('Clean') {
            steps {
                echo "Cleaning project..."
                bat "mvn clean"
            }
        }

        stage('Compile & Install') {
            steps {
                echo "Compiling and installing..."
                bat "mvn install"
            }
        }

        stage('Run Tests') {
            steps {
                echo "Running test cases..."
                bat "mvn test"
            }
        }

        stage('Package Application') {
            steps {
                echo "Packaging application..."
                bat "mvn package"
            }
        }

        stage('Final Output') {
            steps {
                echo "Build Pipeline Completed Successfully!"
            }
        }
    }
}
    }
}
