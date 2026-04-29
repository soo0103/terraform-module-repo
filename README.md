# terraform-module-repo

테라폼으로 시작하는 IaC - AWS EC2 인스턴스를 생성하기 위한 Terraform 모듈 예시입니다.

## Usage

### 1. main.tf 작성

```hcl
provider "aws" {
  region = "ap-northeast-2"
}

module "ec2_seoul" {
  source = "github.com/soo0103/terraform-module-repo/terraform-aws-ec2"
}

output "module_output" {
  value = module.ec2_seoul.private_ip
}
```

### 2. Terraform 초기화
```bash
$ terraform init
```

### 3. 실행 결과 예시
```bash
Initializing the backend...
Initializing modules...
Downloading git::https://github.com/soo0103/terraform-module-repo.git for ec2_seoul...
- ec2_seoul in .terraform\modules\ec2_seoul\terraform-aws-ec2
Initializing provider plugins...
- Reusing previous version of hashicorp/aws from the dependency lock file
- Using previously-installed hashicorp/aws v6.42.0

Terraform has been successfully initialized!
```

### 4. 다운로드된 깃허브에서 관리되는 모듈
```text
.terraform/
└── modules/
    ├── modules.json
    └── ec2_seoul/
        └── terraform-aws-ec2/
            ├── main.tf
            ├── output.tf
            └── variable.tf
```
