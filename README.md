# Get Latest Version

## Linux
api(dot)getfiddler(dot)com/linux/latest-linux

## Mac
api(dot)getfiddler(dot)com/mac/latest-mac

## Windows
api(dot)getfiddler(dot)com/win/latest

## NOTICE

If you are using windows, just try https://github.com/dnSpyEx/dnSpy
## get ilasm (ildasm)

1. dotnet new console -n test
2. cd test
3. dotnet add package Microsoft.NETCore.ILAsm (ILDAsm)
4. dotnet publish -c Release --self-contained --runtime linux-x64
5. export PATH=$(pwd)/bin/Release/netcoreapp3.1/linux-x64/publish:$PATH
6. ilasm (ildasm)

## FiddlerBackendSDK.il

### method FiddlerBackendSDK.User.UserClient::GetBestAccount

from
```c#
public AccountDTO GetBestAccount(UserWithBestAccountDTO user)
{
	if (user.BestEverywhereAccountId != null)
	{
		return user.Accounts.FirstOrDefault((UserAccountDTO x) => x.Id == user.BestEverywhereAccountId.Value);
	}
	return null;
}
```
to
```c#
public AccountDTO GetBestAccount(UserWithBestAccountDTO user)
{
	if (user.BestEverywhereAccountId != null)
	{
		return user.Accounts.FirstOrDefault((UserAccountDTO x) => x.Id == user.BestEverywhereAccountId.Value);
	}
	return user.Accounts.FirstOrDefault();
}
```

## 禁用更新

修改 `.fiddler\Settings\electron-settings.json`，搜索 `autoUpdateSettings` 新增
```json
"autoUpdateSettings": {
    "downloadedUpdateVersion": "0.0.0",
    "disabled":true
}
```

## Some Detail

[Let me see](./DETAIL.MD)
	
## 免责声明
	
本仓库仅供技术学习交流使用，如有下载相关文件，请在学习后24小时内删除相关内容。

请勿将本项目内容用于非法用途，使用者在使用时即视为对行为可能产生的任何不良后果负责。
	
由于传播、利用此工具所提供的信息而造成的任何直接或者间接的后果及损失，均由使用者本人负责，作者不为此承担任何责任。
