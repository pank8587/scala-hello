pipeline {
    agent any

    stages {
        stage("SCM Checkout") {
            steps {
                script {

                    echo "${STAGE_NAME}"

                    if (env.BRANCH_NAME == "staging") {
                        echo "Cloning the Master Branch"

                        git branch: "${env.BRANCH_NAME}", credentialsId: "pankaj", url: "https://github.com/pank8587/scala-hello.git"


                    } else if (env.BRANCH_NAME == "master") {
                        echo "Cloning the release branch"

                        git branch: "${env.BRANCH_NAME}", credentialsId: "pankaj", url: "https://github.com/pank8587/scala-hello.git"


                    } else if (env.BRANCH_NAME == "dev_int") {
                        echo "Cloning the dev_int branch"

                        git branch: "${env.BRANCH_NAME}", credentialsId: "pankaj", url: "https://github.com/pank8587/scala-hello.git"

                    } else {

                        echo "Checkout done in respective branch"

                    }
                }
            }
     
        }

        stage('sbt build') {
            steps {

                sh " echo '${STAGE_NAME}' "

                sh " ${tool name: 'Sbt_Home', type:'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt clean assembly "

                sh " pwd && cd /var/lib/jenkins/workspace/my-appp_master/target/scala-2.10/ && scala hello-world-assembly-0.1-SNAPSHOT.jar "

                sh " echo 'Successfully Build the stage.' "
            }

       
        }


    
    }

    
}
