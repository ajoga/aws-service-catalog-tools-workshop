+++
title = "Creating a new version with CFN Nag enabled"
weight = 440
+++




```yaml
Schema: factory-2019-04-01
Portfolios:
  - DisplayName: central-it-team-portfolio
    Description: A place for self service products ready for your account
    ProviderName: central-it-team
    Associations:
      - arn:aws:iam::${AWS::AccountId}:role/Admin
    Tags:
    - Key: provider
      Value: central-it-team
    Products:
      - Name: account-iam
        Owner: central-it@customer.com
        Description: The iam roles needed for you to do your jobs
        Distributor: central-it-team
        SupportDescription: Contact us on Chime for help #central-it-team
        SupportEmail: central-it-team@customer.com
        SupportUrl: https://wiki.customer.com/central-it-team/self-service/account-iam
        Tags:
        - Key: product-type
          Value: iam
        Versions:
          - Name: v1
            Description: The iam roles needed for you to do your jobs
            Active: True
            Source:
              Provider: CodeCommit
              Configuration:
                RepositoryName: account-iam
                BranchName: v1
          - Name: v2
            Description: The iam roles needed for you to do your jobs
            Active: True
            Options:
              ShouldCFNNag: True
            Source:
              Provider: CodeCommit
              Configuration:
                RepositoryName: account-iam
                BranchName: v1
```