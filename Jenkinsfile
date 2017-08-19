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
            sh 'echo TODO'


    stage 'Amazon Device Lab'
            sh 'echo TODO'


    stage 'Build Release'
        sh "./gradlew assemble"


    stage 'Archive'
        step([$class: 'ArtifactArchiver', artifacts: 'app/build/outputs/apk/*.apk', fingerprint: true])
        step([$class: 'JUnitResultArchiver', testResults: 'app/build/test-results/**/TEST-*.xml'])

}
