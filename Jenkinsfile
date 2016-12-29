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
            }
            
            stage 'Stage 3'
            echo 'should enter stage 3 after completing both 1 and 2'
}
