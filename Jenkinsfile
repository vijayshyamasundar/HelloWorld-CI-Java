node ('master') {
    parallel first:{
                stage 'Stage 1'
                echo 'Stage 1'
                },
            second:{
                stage 'Stage 2'
                echo 'Stage 2'
                writeFile file:'testfile.txt', text:'is this going to append?'
                def fileContent = readFile file:'testfile.txt'
                 echo "$fileContent"
                step([$class: 'ArtifactArchiver', artifacts: '*/txt', excludes: null, fingerprint: true, onlyIfSuccessful: true])
               
            }
            
            stage 'Stage 3'
            echo 'I am on feature-1 branch now'
}
