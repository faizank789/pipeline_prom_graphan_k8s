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
                  git branch: 'main', credentialsId: 'faizank789', url: 'git@github.com:faizank789/pipeline_prom_graphan_k8s.git'
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
                try {
                   sh 'helm repo add prometheus-community https://prometheus-community.github.io/helm-charts'
                   sh 'helm install monitoring prometheus-community/kube-prometheus-stack -f "${values_path}" --wait'
                }
                catch (Exception errorlogs) {
                    println(errorlogs)
                    echo "Registry login issue Please check !"
                }
            }
            }
        }
    }
    }


