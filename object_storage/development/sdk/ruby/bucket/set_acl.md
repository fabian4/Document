### 设置桶的访问控制权限
#### 前提条件
用户拥有易云云存储系统提供的 `access_key` 及 `secret_key` 。

#### 流程说明
1. 初始化 `Client` 实例；
2. 调用 `put_bucket_acl` 方法设置桶的访问控制权限。

#### 示例
```
# 初始化 Client 实例
client = ...

# 设置桶的访问控制权限
acl_policy = {
  grants: [
    {
      grantee: {
        id: 'zc-test-1',
        type: 'CanonicalUser',
      },
      permission: 'FULL_CONTROL',
    },
    {
      grantee: {
        id: 'zc-test-2',
        type: 'CanonicalUser',
      },
      permission: 'READ',
    },
  ],
  owner: {
    id: 'zc-test-1'
  },
}
bucket_name = 'new-bucket'
client.put_bucket_acl(bucket: bucket_name, access_control_plicy: acl_policy)
```
