# Terraform Localstack Dev Container

這個專案示範了如何在 DevContainer 中開發 Terraform 專案，同時使用 LocalStack 來模擬 AWS 服務，以便於本地開發和測試。


## 安裝步驟

1. 啟動 DevContainer 環境

2. 定義一個別名 awslocal 以方便執行 AWS CLI 命令，並使用 LocalStack 作為端點：

    ```bash
    alias awslocal="AWS_ACCESS_KEY_ID=test AWS_SECRET_ACCESS_KEY=test AWS_DEFAULT_REGION=ap-northeast-1 aws --endpoint-url=http://localstack:4566"
    ```

3. 初始化 Terraform 專案：


    ```bash
    terraform init -lock=false
    ```

## 開發流程

1. 計畫變更或建立資源，可使用以下命令計畫和執行：

    ```bash
    terraform plan -lock=false
    terraform apply -lock=false -auto-approve
    ```

2. 檢查 S3 服務以確認資源已被創建：

    ```bash
    awslocal s3 ls s3://test
    ```

3. 撤銷變更或銷毀資源，可使用以下命令計畫和執行：

    ```bash
    terraform plan --destroy
    terraform destroy
    ```
