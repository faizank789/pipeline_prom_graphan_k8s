pipeline {
    agent any

    environment {

        helm_repo="https://prometheus-community.github.io/helm-charts"

        helm_path="/usr/local/bin/helm"
        values_path="charts/kube-prometheus-stack/values.yaml"

    }

    stages {
        stage('Cloning git') {
            steps {
                script { 
                    try { 
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/faizank789/promethus_graphana_helm.git'
            }
             catch (Exception errorlogs) {
                    println(errorlogs)
                    echo " Git Cloning issue ! Please check"
                }
            }
            }
        }


        stage('Installing with Helm') {
            steps {
            script {
                if( ) {
                try {
                   sh 'helm install monitoring prometheus-community/kube-prometheus-stack -f "${values_path}" --wait'
                }
                catch (Exception errorlogs) {
                    println(errorlogs)
                    echo "Registry login issue Please check !"
                }
            }
            else {
                echo "Skipping Logging ECR !"
            }
            }
        }
    }
    }
}


