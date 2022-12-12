pipeline{
  agent{
    label 'slave1'
  }
  stages{
    stage('version-control'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'slave-id', url: 'https://github.com/ukasamgithub/team4-master-slave-demojob.git']]])
      }
    }
    stage('parallel-job'){
      parallel{
        stage('sub-job1'){
          steps{
            echo 'action1'
          }
        }
        stage('sub-job2'){
          agent{
            label 'slave2'
          }
          steps{
            echo 'action2'
          }
        }
        stage('sub-job3'){
            steps{
                sh 'whoami'
            }
        }
      }
    }
    stage('codebuild'){
      agent {
          label 'slave3'
        }
      }
      steps{
        sh 'cat /etc/passwd'
      }
    }
    stage('file creation'){
      agent{
        label 'slave1'
      }
      steps{
        sh 'logname'
      }
    }
}    