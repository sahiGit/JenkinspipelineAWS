pipeline {

    agent any



    stages {

        stage('Pull') {

            steps {

                echo 'Pull stage started'

                // Pull the files from the GitHub repository

                git branch: 'F1', url: 'https://github.com/sahiGit/App.git'

                echo 'Pull stage completed'

            }

        }



        stage('Build') {

            steps {

                echo 'Build stage started'

                // Build the Docker image using the Python file and Dockerfile from GitHub

                sh 'docker build -t myapp-image .'

                echo 'Build stage completed'

            }

        }



        stage('Push') {

            steps {

                echo 'Push stage started'

                // Push the newly created Docker image to Dockerhub repository

                sh 'docker tag myapp-image kubesamm/myapp-image:T1'

                sh 'docker push kubesamm/myapp-image:T1'

                echo 'Push stage completed'

            }

        }



        stage('Deploy') {

            steps {

                echo 'Deploy stage started'

                // Deploy using the deployment.yaml file

                sh 'kubectl apply -f deployment.yaml'

                // Deploy using the service.yaml file

                sh 'kubectl apply -f service.yaml'

                echo 'Deploy stage completed'

            }

        }

    }

}
