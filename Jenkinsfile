pipeline {
    agent any

    environment {

        helm_repo="https://prometheus-community.github.io/helm-charts"
        helm_binary="/usr/local/bin/helm"
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
                    sh '''
                    #!/bin/bash
                   helm repo add prometheus-community "${helm_repo}" && 
                   kubectl create ns monitoring --kubeconfig=$HOME/.kube/config &&
                   helm install monitoring prometheus-community/kube-prometheus-stack -f "${values_path}"
                  '''
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


