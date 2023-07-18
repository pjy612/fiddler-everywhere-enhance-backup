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
1. 全新安装(删除缓存、设置等文件)
2. 登陆并进入到主页, 在尚未下载完新版安装包时退出软件(可通过任务管理器等方式查看网速是否仍被占用来判断是否下载完成)
3. 卸载Fiddler Everywhere, 保留缓存、设置等文件
4. 修改`electron-settings.json`, 在`autoUpdateSettings`下添加`"disabled":true`(见下)
### 注意
1. 理论上不需要第1、2、3步, 只需安装旧版并登陆成功, 退出软件, 修改`electron-settings.json`, 重启软件即可. 如不成功, 需要删除缓存、设置、已下载的安装包, 重新登陆, 修改文件.
2. Fiddler Everywhere 似乎会覆盖`electron-settings.json`的内容.

**`electron-settings.json`文件路径**
- Windows: `%%AppData%%`下, 具体按软件名查找即可(无Windows机器, 欢迎PR)
- Linux: `~/.fiddler/Settings/electron-settings.json`
- macOS: `~/.fiddler/Settings/electron-settings.json`(不知为何与Linux的路径一样, 按理说应该在`/Library/Application Support/Fiddler Everywhere/Caches`下)
  
**`electron-settings.json`修改样例**
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
