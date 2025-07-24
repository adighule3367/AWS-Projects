# Cross-Account S3 Access Using IAM Role – Steps

## 1. Login into Account1
Begin by signing into the primary AWS account (account1).

---

## 2. Create IAM Group and Users
- Create a group and add two users: **User1** and **User2**.
- Attach the following policy to the group:  
  `EC2ReadOnlyAccess`

---

## 3. Attach Policy to Group
Ensure the group has the necessary permissions by attaching the `EC2ReadOnlyAccess` policy.

---

## 4. Login to Second Account (Account 2)
Use a second AWS account (account2).

---

## 5. Create an S3 Bucket
In account 2, create a new S3 bucket.

---

## 6. Create IAM Role in Second Account.
- Create a Role for **Another AWS Account**.
- Insert the **Account ID of account1**.
- Attach `S3ReadOnlyAccess` policy.
- Set **Role Name** to: `S3read`

---

## 7. Update Account1 for Role Access
- Go back to account1:
  - Go to `Group` → `Permission` → `Inline Policy`
  - Select: `AWS Security Token Service`
  - Choose: `Assume Role`
  - Click on `Add Statement` → Apply Policy

---

## 8. Login as IAM User1 (in Account1)
- Login to User1.
- Switch role to the one created in Naksh.
- Check if User1 can see the bucket.

---

## 9. Repeat for User2
Perform same switch role steps with User2.

---

## 10. If Access Denied:
- Login into **Naksh account**.
- Edit the **trusted relationship** of the role.
- Paste the **ARN of User1** into the trust policy.
- Update the policy.

---

## 11. Test Again
- Login as **User1** → Switch Role → Access S3 bucket (should work).

---

## 12. Test as User2
- Login as **User2** → Switch Role → You should get an error (not trusted yet).

---

## Trusted Entity Types (in Role Creation):
- AWS Service  
- Another AWS Account  
- Web Identity  
- SAML 2.0 Federation  

---

✅ **Done!** Now you have a working cross-account access configuration.
