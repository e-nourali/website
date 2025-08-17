pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Deploying website..."
                
                TARGET_DIR=/var/www/mysite

                # کپی کردن فایل‌ها
                cp -r * $TARGET_DIR/

                # تغییر دسترسی‌ها
                sudo chown -R www-data:www-data $TARGET_DIR
                sudo chmod -R 755 $TARGET_DIR
                '''
            }
        }
    }
    triggers {
        githubPush()
    }
}