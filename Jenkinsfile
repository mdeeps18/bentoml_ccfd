node {
         stage("Git Clone"){

         git credentialsId: 'Git-Hub-Credentials', url: "https://github.com/mdeeps18/bentoml_ccfd.git"
         
         stage("Docker build"){
             sh 'docker version'
             sh 'pip install -r requirements.txt'
             sh 'python3 train.py'
             sh 'bentoml build .'
             sh 'bentoml containerize xgb_classifier:latest -t mdeeps18/xgb_classifier:latest'
         
         }
         stage("Docker Login"){
                   
             withCredentials([string(credentialsId: 'mdeeps18', variable: 'PASSWORD')]) {
        	    sh "docker login -u mdeeps18 -p ${PASSWORD}"
         }
         }
         stage("Push image to docker hub"){
             sh 'docker push mdeeps18/xgb_classifier:latest'
         }

         stage("Kubernetes deployment"){
            kubernetesDeploy (configs: 'deploymentservice.yaml', kubeconfigId: 'kuberneteskey')
           }

        }
    }
