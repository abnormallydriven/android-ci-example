node {

    stage 'Checkout'
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/abnormallydriven/android-ci-example.git']]])

    sh "./gradlew clean"

    stage 'Test'

    sh "./gradlew test"



}
