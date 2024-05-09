properties([[$class: 'JiraProjectProperty'], [$class: 'BuildBlockerProperty', blockLevel: <object of type hudson.plugins.buildblocker.BuildBlockerProperty.BlockLevel>, blockingJobs: '', scanQueueFor: <object of type hudson.plugins.buildblocker.BuildBlockerProperty.QueueScanScope>, useBuildBlocker: false], [$class: 'DatadogJobProperty'], gitLabConnection(gitLabConnection: '', jobCredentialId: ''), [$class: 'LeastLoadDisabledProperty', leastLoadDisabled: false], <object of type com.suryagaddipati.jenkins.SlaveUtilizationProperty>, [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobRestrictionProperty'], parameters([[$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', description: 'choose engine', filterLength: 1, filterable: false, name: 'EngineNAME', randomName: 'choice-parameter-3531246406691110', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], oldScript: '', sandbox: true, script: 'return [\'ERROR\']'], script: [classpath: [], oldScript: '', sandbox: true, script: 'return [\'cobalt\',\'azure\']']]], [$class: 'CascadeChoiceParameter', choiceType: 'PT_CHECKBOX', description: 'choose entities', filterLength: 1, filterable: false, name: 'entities', randomName: 'choice-parameter-3531246408272062', referencedParameters: 'EngineNAME', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], oldScript: '', sandbox: true, script: 'return [\'err\']'], script: [classpath: [], oldScript: '', sandbox: true, script: '''if (EngineNAME.equals("cobalt")){
return ["1","2","3"]
} else {
return ["4","5"]
}''']]]]), [$class: 'JobLocalConfiguration', changeReasonComment: '']])

pipeline {
    agent any

    stages {

        stage('Parameters') {
            steps {
                script {
                    properties([
                        parameters([
                            choice(name:"engineName",choices:['Cobalt','Azure'],description: "Choose Engine"),
                            [$class: 'CascadeChoiceParameter',
                                choiceType: 'PT_CHECKBOX',
                                description: 'Select entities',
                                filterLength: 1,
                                filterable: true,
                                name: 'entities',
                                randomName: 'choice-parameter-5631314439613978',
                                script: [
                                    $class: 'GroovyScript',
                                    fallbackScript: [
                                        classpath: [],
                                        sandbox: false,
                                        script:
                                            'return[\'Could not get entities\']'
                                    ],
                                    script: [
                                        classpath: [],
                                        sandbox: false,
                                        script:
                                            '''
                                               if(engineName.equals('Cobalt')){
                                               return["1","2","3"]
                                               } else {
                                               return["4","5","6"]}
                                            '''
                                    ]
                                ]

                            ]

                        ])
                    ])
                }
            }
        }


    }

}

