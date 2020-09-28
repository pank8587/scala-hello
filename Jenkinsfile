pipeline {
    agent any

    tools {nodejs "node"}

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

                sh " ls && cd ui/ && npm install -g grunt-cli bower yo generator-karma generator-angular && npm install npm -g && npm install grunt-contrib-compass --save-dev && npm audit fix && npm install && grunt build --force "

                sh " ${tool name: 'Sbt_Home', type:'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt dist "

                sh " pwd "

                sh " echo 'Successfully Build the stage.' "
            }

       
        }


    
    }

    
}
