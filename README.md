# 🌍 Terraform Providers Lab

In this lab, I learned how Terraform uses providers, how to inspect provider configurations, how provider plugins are downloaded, how to add new resources, and how to identify third-party/community providers installed in various Terraform project directories.

---

## 📋 Lab Overview

**Goal:**

* Understand how Terraform providers work
* Inspect configuration directories to identify provider usage
* Run `terraform init` to download provider plugins
* Create local file resources using the `local` provider
* Add new `.tf` configuration files
* Identify providers downloaded in separate projects

**Learning Outcomes:**

* Use `terraform init`, `terraform plan`, and `terraform apply`
* Read Terraform configuration files and resource blocks
* Understand provider versions and where they are stored
* Inspect `.terraform.lock.hcl` to identify provider details
* Create new Terraform configuration files (`*.tf`)
* Navigate multiple project directories and inspect provider plugins

---

## 🛠 Step-by-Step Journey

---

### **Step 1: Inspect Initial Configuration Directory**

Path:

```
/root/terraform-projects/things-to-do
```

Checked with:

```bash
ls
```

Providers initialized:
✔️ **0 providers**

---

### **Step 2: Initialize Terraform and Check Again**

After running:

```bash
terraform init
```

Providers installed:
✔️ **1 provider** (`local` provider)

---

### **Step 3: Count Configuration Files**

Found:

```
main.tf
```

✔️ Total configuration files: **1**

---

### **Step 4: Count Resource Blocks**

Opened:

```bash
cat main.tf
```

Found **2 resource blocks**.

✔️ Total resources = **2**

---

### **Step 5: Identify Provider Plugin Version**

From:

```
.terraform.lock.hcl
```

Provider version:

```
local = 2.6.1
```

✔️ Local provider version = **2.6.1**

---

### **Step 6: Create Resources (Plan + Apply)**

Ran:

```bash
terraform plan
terraform apply
```

✔️ Resources successfully created in **things-to-do** directory

---

### **Step 7: Navigate to Christmas Wishlist Directory**

Directory:

```
/root/terraform-projects/christmas-wishlist
```

Contains **2 resources**.

---

### **Step 8: Identify Cyberpunk File Output**

Checked:

```bash
cat cyberpunk.tf
```

Filename created by resource:

```
/root/cyberpunk2077.txt
```

✔️ Confirmed file name output

---

### **Step 9: Create a New File `xbox.tf`**

Created:

```bash
vi xbox.tf
```

Added:

```hcl
resource "local_file" "xbox" {
  filename = "/root/xbox.txt"
  content  = "Wouldn't mind an xbox either!"
}
```

Then ran:

```bash
terraform init
terraform plan
terraform apply
```

✔️ New resource created successfully

---

### **Step 10: Inspect Providers in Project provider-A**

Path:

```
/root/terraform-projects/provider-A
```

Checked `.terraform.lock.hcl`
Provider:

```
registry.terraform.io/linode/linode
```

✔️ Provider name: **linode/linode**
✔️ Provider type: **Partner provider**

---

### **Step 11: Inspect Providers in Project provider-B**

Path:

```
/root/terraform-projects/provider-B
```

Checked `.terraform.lock.hcl`
Provider:

```
registry.terraform.io/nbir/nbering/ansible
```

✔️ Provider name: **ansible**
✔️ Provider type: **Community provider**

---

## ✅ Key Commands Summary

| Task                        | Command / Notes       |
| --------------------------- | --------------------- |
| Initialize provider plugins | `terraform init`      |
| View config directory       | `ls`                  |
| Read `.tf` files            | `cat main.tf`         |
| Preview changes             | `terraform plan`      |
| Apply changes               | `terraform apply`     |
| Create new resource file    | `vi xbox.tf`          |
| Destroy resources           | `terraform destroy`   |
| Inspect provider versions   | `.terraform.lock.hcl` |

---

## 💡 Notes / Tips

* Terraform providers are downloaded automatically during `terraform init`.
* Provider version locks are stored in `.terraform.lock.hcl`.
* Local provider resources (`local_file`) are useful for beginner labs.
* Each project directory maintains its **own** provider plugins.
* Partner and community providers expand Terraform’s capabilities.
* Always run `terraform init` after adding new `.tf` files or providers.

---

## 📌 Lab Summary

| Step                       | Status | Key Takeaways                |
| -------------------------- | ------ | ---------------------------- |
| Inspect providers          | ✅      | Started with 0 → installed 1 |
| Count configs              | ✅      | Found `main.tf`              |
| Count resources            | ✅      | 2 resource blocks            |
| Identify provider version  | ✅      | local v2.6.1                 |
| Apply resources            | ✅      | Created files in project     |
| Explore Christmas wishlist | ✅      | Found new outputs            |
| Add `xbox.tf`              | ✅      | Resource created             |
| Provider-A inspection      | ✅      | Found Linode provider        |
| Provider-B inspection      | ✅      | Found Ansible provider       |

---

## ✅ References

* [Terraform Providers Overview](https://developer.hashicorp.com/terraform/language/providers)
* [Local Provider Documentation](https://registry.terraform.io/providers/hashicorp/local/latest/docs)
* [Terraform Files & Directory Structure](https://developer.hashicorp.com/terraform/language/files)
* [Provider Installation & Lock Files](https://developer.hashicorp.com/terraform/language/providers/configuration)
