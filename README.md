
tools{ jdk 'JAVA_HOME' maven 'MAVEN_HOME' } stages { stage('git repo & clean') { steps { bat "rmdir /s /q Harshitha_Jenkins_Maven || exit 0" bat "git clone https://github.com/Harshitha-Macha/Harshitha_Jenkins_Maven.git" bat "mvn clean -f Harshitha_Jenkins_Maven/pom.xml" } } stage('install') { steps { bat "mvn install -f Harshitha_Jenkins_Maven/pom.xml" } } stage('test') { steps { bat "mvn test -f Harshitha_Jenkins_Maven/pom.xml" } } stage('package') { steps { bat "mvn package -f Harshitha_Jenkins_Maven/pom.xml" } }

//-------------------------------------------------------------------------------------------------------

pipeline { agent any

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
} } }

Start Minikube Open CMD or PowerShell: minikube start 2️⃣ Create an nginx server kubectl create deployment mynginx --image=nginx Check: kubectl get pods 3️⃣ Expose the deployment kubectl expose deployment mynginx --type=NodePort --port=80 4️⃣ Scale to 4 pods kubectl scale deployment myapp --replicas=4 ->Port forwarding: kubectl port-forward svc/myapp 8081:80 8081 can be replaced by any ->Kubernets dashboard Minikube dashboard ->Stopping kubectl delete deployment mynginx kubectl delete service mynginx minikube stop

⭐ PART 2 — Nagios in Docker 1️⃣ Pull image docker pull jasonrivers/nagios 2️⃣ Run Nagios docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios 3️⃣ Open browser Go to: http://localhost:8888 Login: • username: nagiosadmin • password: nagios
