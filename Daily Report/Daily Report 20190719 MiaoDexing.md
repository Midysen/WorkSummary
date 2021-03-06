# PROTECTION_NORMAL类权限
- 当用户安装或更新应用时，系统将授予应用所请求的属于 PROTECTION_NORMAL 的所有权限（安装时授权的一类基本权限）。这类权限包括：

android.permission.ACCESS LOCATIONEXTRA_COMMANDS <br>
android.permission.ACCESS NETWORKSTATE <br>
android.permission.ACCESS NOTIFICATIONPOLICY <br>
android.permission.ACCESS WIFISTATE <br>
android.permission.ACCESS WIMAXSTATE <br>
android.permission.BLUETOOTH <br>
android.permission.BLUETOOTH_ADMIN <br>
android.permission.BROADCAST_STICKY <br>
android.permission.CHANGE NETWORKSTATE <br>
android.permission.CHANGE WIFIMULTICAST_STATE <br>
android.permission.CHANGE WIFISTATE <br>
android.permission.CHANGE WIMAXSTATE <br>
android.permission.DISABLE_KEYGUARD <br>
android.permission.EXPAND STATUSBAR <br>
android.permission.FLASHLIGHT <br>
android.permission.GET_ACCOUNTS <br>
android.permission.GET PACKAGESIZE <br>
android.permission.INTERNET <br>
android.permission.KILL BACKGROUNDPROCESSES <br>
android.permission.MODIFY AUDIOSETTINGS <br>
android.permission.NFC <br>
android.permission.READ SYNCSETTINGS <br>
android.permission.READ SYNCSTATS <br>
android.permission.RECEIVE BOOTCOMPLETED <br>
android.permission.REORDER_TASKS <br>
android.permission.REQUEST INSTALLPACKAGES <br>
android.permission.SET TIMEZONE <br>
android.permission.SET_WALLPAPER <br>
android.permission.SET WALLPAPERHINTS <br>
android.permission.SUBSCRIBED FEEDSREAD <br>
android.permission.TRANSMIT_IR <br>
android.permission.USE_FINGERPRINT <br>
android.permission.VIBRATE <br>
android.permission.WAKE_LOCK <br>
android.permission.WRITE SYNCSETTINGS <br>
com.android.alarm.permission.SET_ALARM <br>
com.android.launcher.permission.INSTALL_SHORTCUT <br>
com.android.launcher.permission.UNINSTALL_SHORTCUT <br>

这类权限只需要在AndroidManifest.xml中简单声明这些权限就好，安装时就授权。不需要每次使用时都检查权限，而且用户不能取消以上授权。

# 权限控制组

Permission Group|Permissions
---|---|
CALENDAR| · READ_CALENDAR <br>  · WRITE_CALENDAR
CAMERA| · CAMERA
CONTACTS|· READ_CONTACTS <br>· WRITE_CONTACTS <br>· GET_ACCOUNTS
LOCATION | 	· ACCESS_FINE_LOCATION <br>· ACCESS_COARSE_LOCATION
MICROPHONE | 	· RECORD_AUDIO
PHONE |· READ_PHONE_STATE <br> · CALL_PHONE <br> · READ_CALL_LOG <br> · WRITE_CALL_LOG <br> · ADD_VOICEMAIL <br> · USE_SIP <br> · PROCESS_OUTGOING_CALLS
SENSORS |    BODY_SENSORS
SMS | · SEND_SMS <br> · RECEIVE_SMS <br> · READ_SMS <br> · RECEIVE_WAP_PUSH <br> · RECEIVE_MMS
STORAGE | · READ_EXTERNAL_STORAGE <br> · WRITE_EXTERNAL_STORAGE

# 处理不再提醒
- 如果用户拒绝某授权,下一次弹框，用户会有一个“不再提醒”的选项的来防止app以后继续请求授权。如果这个选项在拒绝授权前被用户勾选了。下次为这个权限请求requestPermissions时，对话框就不弹出来了，系统会直接回调onRequestPermissionsResult函数，回调结果为最后一次用户的选择。所以为了应对这种情况，系统提供了一个shouldShowRequestPermissionRationale()函数，这个函数的作用是帮助开发者找到需要向用户额外解释权限的情况，这个函数：
1. 应用安装后第一次访问，直接返回false；第一次请求权限时，用户拒绝了，下一次shouldShowRequestPermissionRationale()返回 true，这时候可以显示一些为什么需要这个权限的说明；
2. 第二次请求权限时，用户拒绝了，并选择了“不再提醒”的选项时：shouldShowRequestPermissionRationale()返回 false；设备的系统设置中禁止当前应用获取这个权限的授权，shouldShowRequestPermissionRationale()返回false；　　
3. 注意：第二次请求权限时，才会有“不再提醒”的选项，如果用户一直拒绝，并没有选择“不再提醒”的选项，下次请求权限时，会继续有“不再提醒”的选项，并且shouldShowRequestPermissionRationale()也会一直返回true。

# 读取系统里的packages.xml
- ./services/core/java/com/android/server/pm/Settings.java
```
 439         mSettingsFilename = new File(mSystemDir, "packages.xml");                                                                                                                                      
 440         mBackupSettingsFilename = new File(mSystemDir, "packages-backup.xml");
 441         mPackageListFilename = new File(mSystemDir, "packages.list");
 442         FileUtils.setPermissions(mPackageListFilename, 0640, SYSTEM_UID, PACKAGE_INFO_GID);

3085                 String tagName = parser.getName();                                                                                                                                                     
3086                 if (tagName.equals("package")) {
3087                     readPackageLPw(parser);
3088                 } else if (tagName.equals("permissions")) {
3089                     readPermissionsLPw(mPermissions, parser);
3090                 } else if (tagName.equals("permission-trees")) {
3091                     readPermissionsLPw(mPermissionTrees, parser);
3092                 } else if (tagName.equals("shared-user")) {
3093                     readSharedUserLPw(parser);


```
在packages.xml里permissions放在前面，所以这里先读的是permissions section, permissions字段,保存到mSettings.mPermissions，permissions是所有apk自定义的permissions

- readInstallPermissionsLPr
```
2211     void readInstallPermissionsLPr(XmlPullParser parser,
2212             PermissionsState permissionsState) throws IOException, XmlPullParserException {
2213         int outerDepth = parser.getDepth();
2214         int type;
2215         while ((type=parser.next()) != XmlPullParser.END_DOCUMENT
2216                 && (type != XmlPullParser.END_TAG
2217                 || parser.getDepth() > outerDepth)) {
2218             if (type == XmlPullParser.END_TAG
2219                     || type == XmlPullParser.TEXT) {
2220                 continue;
2221             }
2222             String tagName = parser.getName();
2223             if (tagName.equals(TAG_ITEM)) {
2224                 String name = parser.getAttributeValue(null, ATTR_NAME);
2225 
2226                 BasePermission bp = mPermissions.get(name);
2227                 if (bp == null) {
2228                     Slog.w(PackageManagerService.TAG, "Unknown permission: " + name);
2229                     XmlUtils.skipCurrentTag(parser);
2230                     continue;
2231                 }
2232 
2233                 String grantedStr = parser.getAttributeValue(null, ATTR_GRANTED);
2234                 final boolean granted = grantedStr == null
2235                         || Boolean.parseBoolean(grantedStr);
2236 
2237                 String flagsStr = parser.getAttributeValue(null, ATTR_FLAGS);
2238                 final int flags = (flagsStr != null)
2239                         ? Integer.parseInt(flagsStr, 16) : 0;
2240 
2241                 if (granted) {
2242                     if (permissionsState.grantInstallPermission(bp) ==                                                                                                                                 
2243                             PermissionsState.PERMISSION_OPERATION_FAILURE) {
2244                         Slog.w(PackageManagerService.TAG, "Permission already added: " + name);
2245                         XmlUtils.skipCurrentTag(parser);
2246                     } else {
2247                         permissionsState.updatePermissionFlags(bp, UserHandle.USER_ALL,
2248                                 PackageManager.MASK_PERMISSION_FLAGS, flags);
2249                     }
2250                 } else {
2251                     if (permissionsState.revokeInstallPermission(bp) ==
2252                             PermissionsState.PERMISSION_OPERATION_FAILURE) {
2253                         Slog.w(PackageManagerService.TAG, "Permission already added: " + name);
2254                         XmlUtils.skipCurrentTag(parser);
2255                     } else {
2256                         permissionsState.updatePermissionFlags(bp, UserHandle.USER_ALL,
2257                                 PackageManager.MASK_PERMISSION_FLAGS, flags);
2258                     }
2259                 }

```
- grantInstallPermission
```
services/core/java/com/android/server/pm/PermissionsState.java

177     /**
178      * Grant an install permission.
179      *           
180      * @param permission The permission to grant.
181      * @return The operation result which is either {@link #PERMISSION_OPERATION_SUCCESS},
182      *     or {@link #PERMISSION_OPERATION_SUCCESS_GIDS_CHANGED}, or {@link
183      *     #PERMISSION_OPERATION_FAILURE}.
184      */                      
185     public int grantInstallPermission(BasePermission permission) {
186         return grantPermission(permission, UserHandle.USER_ALL);                                                                                                                                        
187     }        



559     private int grantPermission(BasePermission permission, int userId) {                                                                                                                                
560         if (hasPermission(permission.name, userId)) {
561             return PERMISSION_OPERATION_FAILURE;
562         }
563 
564         final boolean hasGids = !ArrayUtils.isEmpty(permission.computeGids(userId));
565         final int[] oldGids = hasGids ? computeGids(userId) : NO_GIDS;
566 
567         PermissionData permissionData = ensurePermissionData(permission);
568 
569         if (!permissionData.grant(userId)) {
570             return PERMISSION_OPERATION_FAILURE;
571         }
572     
573         if (hasGids) {
574             final int[] newGids = computeGids(userId);
575             if (oldGids.length != newGids.length) {
576                 return PERMISSION_OPERATION_SUCCESS_GIDS_CHANGED;
577             }
578         }
579 
580         return PERMISSION_OPERATION_SUCCESS;
581     }



657 public PermissionData(PermissionData other) {
658             this(other.mPerm);
659             final int otherStateCount = other.mUserStates.size();
660             for (int i = 0; i < otherStateCount; i++) {
661                 final int otherUserId = other.mUserStates.keyAt(i);
662                 PermissionState otherState = other.mUserStates.valueAt(i);                                                                                                                              
663                 mUserStates.put(otherUserId, new PermissionState(otherState));
664             }

```

- 这些安装权限是apk在安装时自动grant的，都是normal的等级，不是dangeous权限。
该函数的主要作用是:
  -  生成permission对应的PermissionData，并用加入到PermissionsState mPermissions里
  -  针对用户id,grant权限，生成PermissionState对象，并用mUserStates来track.
 
 - 注意：如果是系统第一次开机的时候，系统里是没有package.xml的，那么将不会生成package对应的PackageSetting, 在这种情况下，PackageSetting会在扫描apk文件时进行生成.

# 扫描系统apk文件，解析apk文件
1、 
```
scanDirLI -> scanPackageLI(file, …) ->
   pkg = pp.parsePackage(scanFile, parseFlags); //解析apk文件
      parseClusterPackage
      pkg = parseBaseApk(baseApk, assets, flags);
        PackageParser.Package pkg = parseBaseApk(res, …) //解析apk中的AndroidManifest.xml
```
其中PackageParser.Package代表一个解析出来的apk, 而PackageParser指的是一个解析类。

2、 
```
scanPackageLI(pkg, xxx) -> scanPackageDirtyLI(pkg, …)
```
该步骤与Permission相关的的操作主要是解析pkg即PackageParser.Package里的字段，将apk相关的信息保存到PackageManagerService里或mSettings里；
根据pkg里解析出来的信息生成PackageSetting
```
pkgSetting = mSettings.getPackageLPw(pkg, …)
        PackageSetting p = getPackageLPw(name, …)
     //如果系统第一次开机启动，那么从Setting里是拿不到PackageSetting的，这时只能新生成一个，
     //并将它通过addPackageSettingLPw加入到mSettings.mPackages里;
     //如果不是第一次开机，那么将会直接从Settings.mPackages里取
```

# 更新permissions
- 分为两种情况
  -  在读取package.xml的时候已经grant了
  -  第一次开机，updatePermissionsLPw 会 grant相应的权限

```
updatePermissionsLPw(null, null, updateFlags)->grantPermissionsLPw(pkg, …)
//为每个package grant所请求的permissions

void grantPermissionsLPw(PackageParser.Package pkg, boolean replace, String packageOfInterest) {

final PackageSetting ps = (PackageSetting) pkg.mExtras;
if (ps == null) { return; }
//获得package的PackageSettings

PermissionsState permissionsState = ps.getPermissionsState();
//获得package的PermissionState类
PermissionsState origPermissions = permissionsState;

final int N = pkg.requestedPermissions.size();
for (int i=0; i<N; i++) { //遍历当前所有请求的permissions，即<uses-permission>
    final String name = pkg.requestedPermissions.get(i);
                   //获得permisison name
    final BasePermission bp = mSettings.mPermissions.get(name);
                  //根据permission name获得permission所表示的结构
final int level = bp.protectionLevel & PermissionInfo.PROTECTION_MASK_BASE;
                  //获得permission的等级
switch (level) {
    case PermissionInfo.PROTECTION_NORMAL: {grant = GRANT_INSTALL}
    case PermissionInfo.PROTECTION_DANGEROUS: {grant = GRANT_RUNTIME;}
    case PermissionInfo.PROTECTION_SIGNATURE: {}
}

switch (grant) {
    case GRANT_INSTALL: {
    permissionsState.grantInstallPermission(bp)
         //为所有用户颁布安装permission，即生成permission对应的PermissionState
         //并用PermissionData的mUserStates来track
         //其实这里grant install的操作在之前 readLPw就已经执行过了，这里没什么实际用处，主要是对sharedUser 进行一些update ?????

    case GRANT_RUNTIME: {
 }
}
```

# grant默认的runtime 权限
```
mPackageManagerService.systemReady();  
int[] grantPermissionsUserIds = EMPTY_INT_ARRAY;
for (int userId : UserManagerService.getInstance().getUserIds()) {
    if (!mSettings.areDefaultRuntimePermissionsGrantedLPr(userId)) {
        grantPermissionsUserIds = ArrayUtils.appendInt(
                grantPermissionsUserIds, userId);
    }
}

// 如果是系统第一次启动，即没有runtime-permissions.xml, 那么系统会进入grant default permission的阶段.

for (int userId : grantPermissionsUserIds) {
    mDefaultPermissionPolicy.grantDefaultPermissions(userId);
}
```
- 为系统级的app grant默认runtime权限
```
public void grantDefaultPermissions(int userId) {
    grantPermissionsToSysComponentsAndPrivApps(userId);
    grantDefaultSystemHandlerPermissions(userId);
}

void grantPermissionsToSysComponentsAndPrivApps(int userId) {
  for (PackageParser.Package pkg : mService.mPackages.values()) {
  if (!isSysComponentOrPersistentPlatformSignedPrivAppLPr(pkg)
        || !doesPackageSupportRuntimePermissions(pkg)
        || pkg.requestedPermissions.isEmpty()) {
   /*
   过滤出特定的apk, 
   1, sdk version >= 23的 
   2, platform签名 
   3, persistent privilege App进行 grant runtime权限
   */
    continue;
  }

  Set<String> permissions = new ArraySet<>();
  final int permissionCount = pkg.requestedPermissions.size();
  for (int i = 0; i < permissionCount; i++) {
    String permission = pkg.requestedPermissions.get(i);
    BasePermission bp = mService.mSettings.mPermissions.get(permission);
    if (bp != null && bp.isRuntime()) {
        permissions.add(permission);
    }
  }
  if (!permissions.isEmpty()) {
    grantRuntimePermissionsLPw(pkg, permissions, true, userId);
 }

void grantRuntimePermissionsLPw(PackageParser.Package pkg, Set<String> permissions, boolean systemFixed, boolean overrideUserChoice,  int userId) {
 mService.grantRuntimePermission(pkg.packageName, permission, userId);
 mService.updatePermissionFlags (permission, pkg.packageName,
        newFlags, newFlags, userId);
}

void grantRuntimePermission(String packageName, String name, final int userId) {
    int result = permissionsState.grantRuntimePermission(bp, userId);
    mOnPermissionChangeListeners.onPermissionsChanged(uid);
    mSettings.writeRuntimePermissionsForUserLPr(userId, false);
}
```
# Shared User ID 的权限
- 在packages.xml 和 runtime-permissions.xml里有一节是 <shared-user>, 表示的是这个UID所获得的权限。在packages.xml或runtime-permissions.xml里会发现如果拥有相同uid的package，它们的grant 权限和UID在shared-user里获得的权限是一样的。（因为拥有相同UID, 且签名一样的话，他们可以彼此访问数据，理所当然应该获得所有的相同的权限）。
 - SharedUserSettings继承于SettingBase, 因此也就有PermissionsState 权限状态类
