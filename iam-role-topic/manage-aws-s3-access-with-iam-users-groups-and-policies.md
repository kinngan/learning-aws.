# Manage AWS S3 access with IAM users, groups and policies

## Mục tiêu
Tài liệu này hướng dẫn cơ bản cách quản lý truy cập tới AWS S3 bằng IAM Users, Groups và Policies—bao gồm ví dụ policy JSON và các bước cấu hình.

## Yêu cầu trước
- Có tài khoản AWS với quyền tạo IAM & S3.
- AWS Management Console hoặc AWS CLI cấu hình sẵn.

## Khái niệm nhanh
- **IAM User:** Người/ứng dụng cá nhân cần truy cập resource.
- **IAM Group:** Tập hợp Users, gán policy chung cho nhóm.
- **IAM Policy:** Quy tắc (JSON) cho phép/deny hành động trên resource (ví dụ: S3 bucket).
- **IAM Role:** Vai trò có thể được assumable bởi EC2, Lambda, hoặc user bên ngoài.

## Ví dụ: Policy chỉ cho phép đọc bucket cụ thể
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::example-bucket",
        "arn:aws:s3:::example-bucket/*"
      ]
    }
  ]
}
