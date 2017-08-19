node {

    stage 'Checkout'
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/abnormallydriven/android-ci-example.git']]])
        sh "./gradlew clean"


    stage 'Unit Test'
        sh "./gradlew test"


    stage 'Assemble Android Test'
        sh "./gradlew assembleDebug"
        sh "./gradlew assembleDebugAndroidTest"


    stage 'Cloud Test Lab'
        sh "gcloud auth activate-service-account --key-file /opt/service_account_key.json"
        sh "gcloud firebase test android run --app app/build/outputs/apk/app-debug.apk --test app/build/outputs/apk/app-debug-androidTest.apk --device model=Nexus6,version=21,locale=en,orientation=portrait"


    stage 'Amazon Device Lab'
            sh 'echo TODO'


    stage 'Build Release'
        sh "./gradlew assemble"


    stage 'Archive'
        step([$class: 'ArtifactArchiver', artifacts: 'app/build/outputs/apk/*.apk', fingerprint: true])
        step([$class: 'JUnitResultArchiver', testResults: 'app/build/test-results/**/TEST-*.xml'])

}
