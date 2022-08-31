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

     stage('Checking helm Package')  {
        steps {
            script {
                try {
                    sh '''
                    #!/bin/bash
                    if ! [[ env.helm_binary ]] ; then
                       echo "Not Found Helm Package !"
                    fi
                    '''
                }
                catch (Exception errorlogs) {
                    println(errorlogs)
                    echo " something for helm package please check !"
                }
            }
        }
     }




    //     stage('Installing with Helm') {
    //         steps {
    //         script {   
    //             try {
    //                 sh '''
    //                 #!/bin/bash
    //                namespace=`kubectl get ns monitoring`
    //                if ! [[ $namespace ]] ; then
    //                kubectl create ns monitoring 
    //                fi
    //                helm repo add prometheus-community "${env.helm_repo}" &&
    //                helm install monitoring prometheus-community/kube-prometheus-stack -f "${env.values_path} --wait"
    //               '''
    //             }
    //             catch (Exception errorlogs) {
    //                 println(errorlogs)
    //                 echo "Registry login issue Please check !"
    //             }
    //         }
    //         }
    //     }
     }
    }


