# Azure DevOps

## Run pipeline from REST
```bash
curl --location --request POST 'https://dev.azure.com/<organisation>/<project>/_apis/pipelines/<definitionId_or_buildNumber>/runs?api-version=6.0-preview.1' \
        --header 'Authorization: Basic <BASE64TOKEN>' \
        --header 'Content-Type: application/json' \
        --data-raw '{
                "templateParameters": {
                	"<variable>": "<value>"
            }
        }'
```

## Insert multiline into variable
```yaml
    - task: CmdLine@2
      inputs:
        script: |
          # Return string variables separated by comma (ex: 3.6-alpine,3.6.12,...) and replace comma with "$OA"
          IMAGE_TAGS=$(grep '#TAGS' ${{ parameters.path_to_dockerfile }}/Dockerfile | cut -d= -f2 | sed "s/,/%0A/g")

          # Export variables to use it in other tasks
          echo "##vso[task.setvariable variable=imageTags]${IMAGE_TAGS}"
```
