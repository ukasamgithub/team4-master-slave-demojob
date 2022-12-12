pipeline{
  agent {
  }
  stages{
    stage('version-control'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'slave-id', url: 'https://github.com/ukasamgithub/team4-master-slave-demojob.git']]])
      }
    }
    sage('parallel-job'){
      parallel{
        stage('sub-job1'){
          steps{
            echo 'action1'
          }
        }
        stage('sub-job2'){
          steps{
            echo 'action2'
          }
        }
        stage('sub-job3'){
            steps{
                echo 'action3'
            }
        }
      }
    }
    stage('codebuild'){
      agent {
        label {
          label 'slave3'
        }
      }
      steps{
        sh 'cat /etc/passwd'
      }
      stage('file creation'){
        agent{
          label 'slave1'
        }
        staeps{
          sh 'touch gropu5.txt'
        }
      }
      stage('identification'){
        agent{
          label 'slave2'
        }
        steps{
          sh 'logname'
        }
      }
    }
  }
}
