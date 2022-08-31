pipeline {
    agent any

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

     stage('Checking helm Package')  {
        steps {
            script {
                try {
                    sh '''
                    #!/bin/bash
                    helm_binary=`ls /usr/local/bin/helm`
                    if ! [[ $helm_binary ]] ; then
                       curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 && \
                       chmod 700 get_helm.sh && \
                       ./get_helm.sh
                    fi
                    '''
                }
                catch (Exception errorlogs) {
                    println(errorlogs)
                    echo " something wrong for helm package please check !"
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
                    helm_repo="https://prometheus-community.github.io/helm-charts"
                    values_path="charts/kube-prometheus-stack/values.yaml"
                    namespace=monitoring
                   helm repo add prometheus-community $helm_repo && \
                   helm install monitoring prometheus-community/kube-prometheus-stack -f $values_path --namespace $namespace --wait"
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


