pipeline {
    agent any
    // environment {
    //     NAME = 'small-tools-web'
    //     PROFILE = 'dev'
    //     APP = 'registry.cn-hangzhou.aliyuncs.com/zhengqing/small-tools-web:dev'
    //     APP_PORT = 80
    // }

    stages {
        stage('拉取代码') {
            steps {
                echo '****************************** download code start... ******************************'
                git branch: 'main',  url: 'https://github.com/killonepersonintensteps/cicd_test.git'
            }
        }

        stage('构建静态文件') {
            steps {
                echo '****************************** vue start... ******************************'
                sh 'node --version'
                sh 'npm --version'
                sh 'npm config get registry'
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('部署阶段') {
            steps {
                echo '****************************** delete container and image... ******************************'
                sh 'cp -R ./dist ~/Desktop/dist'
            }
        }

        // stage('运行容器') {
        //     steps {
        //         echo '****************************** run start... ******************************'
        //         sh 'docker run -d -p $APP_PORT:80 --restart=always --name $NAME $APP'
        //     }
        // }
    }
}
