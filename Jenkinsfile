pipeline {
    agent any

    environment {

        helm_repo="https://prometheus-community.github.io/helm-charts"

        helm_path="/usr/local/bin/helm"

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
        
        stage('checking if Helm found') {
            steps {
            script {
                if (!env.helm_path)
                try {
                 echo "Helm not found Installing"
                    sh '''
                    #!/bin/bash
                   sudo curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 
                   sudo  chmod 700 get_helm.sh
                   sudo bash get_helm.sh
                    '''
                }
                catch (Exception errorlogs) {
                    println(errorlogs)
                    echo "something wrong while installation helm | Please check !"  
                }
            }
            }
        }



    //     stage('Installing with Helm') {
    //         steps {
    //         script {
    //             if( ) {
    //             try {
    //                 sh 'helm install consul --wait --values helm-consul-values.yml'
    //                 helm install monitoring prometheus-community/kube-prometheus-stack -f values.yaml --wait
    //             }
    //             catch (Exception errorlogs) {
    //                 println(errorlogs)
    //                 echo "Registry login issue Please check !"
    //             }
    //         }
    //         else {
    //             echo "Skipping Logging ECR !"
    //         }
    //         }
    //     }
    // }
    // }
}
}
