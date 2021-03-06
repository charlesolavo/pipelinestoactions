### Azure Pipelines
[Azure SQL DacpacTask](https://github.com/microsoft/azure-pipelines-tasks/tree/master/Tasks/SqlAzureDacpacDeploymentV1)

- Classic

![Azure SQL](images/task-AzureSQL.png)

- YAML

```yaml
steps:
- task: SqlAzureDacpacDeployment@1
  displayName: 'Azure SQL DacpacTask'
  inputs:
    azureSubscription: '[Subscription Name]'
    ServerName: '$(SQLServer)'
    DatabaseName: '$(SQLDatabase)'
    SqlUsername: '$(Login)'
    SqlPassword: '$(Pwd)'
    DacpacFile: '$(System.DefaultWorkingDirectory)/_[Project Name]/drop/[Project Name]/bin/Release/[Project Name].dacpac'
  ```
### GitHub Actions
[Azure SQL Deploy](https://github.com/marketplace/actions/azure-sql-deploy)
```yaml
- name: Azure SQL Deploy
  uses: Azure/sql-action@v1
  with:
    server-name: {% raw  %}${{secrets.SQL_SERVERNAME}}{% endraw %}
    connection-string: {% raw  %}${{secrets.AZURE_SQL_CONNECTION_STRING}}{% endraw %}
    dacpac-package: ./[Project Name]/bin/{% raw  %}${{env.buildConfiguration}}{% endraw %}/[Project Name].dacpac
```
