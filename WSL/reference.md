---
title: Windows Subsystem for Linux のコマンド リファレンス
description: Windows Subsystem for Linux を管理するコマンドの一覧
keywords: BashOnWindows, bash, wsl, windows, windows subsystem for linux, windowssubsystem, ubuntu
ms.date: 07/31/2017
ms.topic: article
ms.assetid: 82908295-a6bd-483c-a995-613674c2677e
ms.custom: seodec18
ms.localizationpriority: high
ms.openlocfilehash: d74a6926fd797f2e1ede0fd5d8d080d0f1ce3f6b
ms.sourcegitcommit: 0b5a9f8982dfff07fc8df32d74d97293654f8e12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71269843"
---
# <a name="command-reference-for-windows-subsystem-for-linux"></a>Windows Subsystem for Linux のコマンド リファレンス

Windows Subsystem for Linux を操作する最良の方法は、`wsl.exe` コマンドを使用することです。 


## `wsl.exe`

Windows バージョン 1903 以降で `wsl.exe` を使用する場合のすべてのオプションを含む一覧を次に示します。

使用法: `wsl [Argument] [Options...] [CommandLine]`

### <a name="arguments-for-running-linux-binaries"></a>Linux バイナリを実行するための引数

* **引数なし**

  コマンド ラインが指定されていない場合、wsl.exe で既定のシェルが起動されます。

* **--exec、-e \<CommandLine>**
  
  既定の Linux シェルを使用せずに、指定したコマンドを実行します。

* **--**
  
  残りのコマンドラインをそのまま渡します。

上記のコマンドでは、次のオプションも使用できます。

* **--distribution、-d \<Distro>**

  指定されたディストリビューションを実行します。

* **--user、-u \<UserName>**

  指定されたユーザーとして実行します。

### <a name="arguments-for-managing-windows-subsystem-for-linux"></a>Windows Subsystem for Linux を管理するための引数

* **--export \<Distro> \<FileName>**
  
  ディストリビューションを tar ファイルにエクスポートします。 標準出力の場合、ファイル名は - でもかまいません。

* **--import \<Distro> \<InstallLocation> \<FileName>**
  
  指定した tar ファイルを新しいディストリビューションとしてインポートします。 標準入力の場合、ファイル名は - でもかまいません。

* **--list、-l [Options]**
  
  ディストリビューションを一覧表示します。

  オプション:
  * **--all**
      
    現在インストール中またはアンインストール中のディストリビューションを含む、すべてのディストリビューションを一覧表示します。

  * **--running**
      
    現在実行中のディストリビューションのみを一覧表示します。

* **--set-default、-s \<Distro>**
  
  このディストリビューションを既定値として設定します。

* **--terminate、-t \<Distro>**
  
  指定されたディストリビューションを終了します。

* **--unregister \<Distro>**
  
  ディストリビューションの登録を解除します。
   
* **--help** 使用方法に関する情報を表示します。

## <a name="additional-commands"></a>その他のコマンド

Windows Subsystem for Linux を操作するための過去のコマンドもあります。 これらの機能は、`wsl.exe` 内に含まれますが、引き続き使用できます。 

### `wslconfig.exe`

このコマンドでは、WSL ディストリビューションを構成できます。 そのオプションの一覧を次に示します。

使用法: `wslconfig [Argument] [Options...]`

#### <a name="arguments"></a>引数
* **/l、/list [Options]**
  
  登録済みのディストリビューションを一覧表示します。
  
  オプション:
    * **/all**
    
      現在インストール中またはアンインストール中のディストリビューションを含む、すべてのディストリビューションをオプションで一覧表示します。

    * **/running**
      
      現在実行中のディストリビューションのみを一覧表示します。

* **/s、/setdefault \<Distro>**
  
  このディストリビューションを既定値として設定します。

* **/t、/terminate \<Distro>**
  
  ディストリビューションを終了します。

* **/u、/unregister \<Distro>**
  
  ディストリビューションの登録を解除します。
   
* **/upgrade \<Distro>**
  
  ディストリビューションを WslFs ファイル システム形式にアップグレードします。

### `bash.exe`

このコマンドは、bash シェルを開始するために使用されます。 このコマンドで使用できるオプションを次に示します。

使用法: `bash [Options...]`

* **オプションの指定なし**
  
  現在のディレクトリで Bash シェルを起動します。 Bash シェルがインストールされていない場合は、`lxrun /install` が自動的に実行されます。

* **~**
  
  `bash ~` で、ユーザーのホームディレクトリに bash シェルが起動されます。  `cd ~` の実行と似ています。

* **-c "\<command>"**
  
  コマンドを実行し、出力を行って、Windows のコマンド プロンプトに戻ります。
    
  例: `bash -c "ls"` のようにします。

## <a name="deprecated-commands"></a>非推奨のコマンド

`lxrun.exe` は、Windows Subsystem for Linux をインストールして管理するために使用された最初のコマンドでした。 これは、Windows 10 1803 以降では非推奨です。

`lxrun.exe` コマンドは、[Windows Subsystem for Linux (WSL)](https://msdn.microsoft.com/en-us/commandline/wsl/faq#what-windows-subsystem-for-linux-wsl-) を直接操作するために使用できます。  これらのコマンドは `\Windows\System32` ディレクトリにインストールされ、Windows コマンド プロンプトまたは PowerShell 内で実行できます。

| コマンド                     | 説明                     |
|:----------------------------|:---------------------------|
| `lxrun`                     | lxrun コマンドは、WSL インスタンスの管理に使用されます。 |
| `lxrun /install`            | ダウンロードとインストールのプロセスを開始します。 <br/> **/y** を追加すると、すべてのプロンプトを省略できます。  確認プロンプトが自動的に受け入れられ、既定のユーザーはルートに設定されます。          |
| `lxrun /uninstall`          | Ubuntu イメージをアンインストールして削除します。  既定では、これで、ユーザーの Ubuntu ホーム ディレクトリは削除されません。 <br/> **/y** を追加すると、確認プロンプトを自動的に受け入れることができます。 <br/>**/full** を指定すると、ユーザーの Ubuntu ホーム ディレクトリをアンインストールして削除します。         |
| `lxrun /setdefaultuser <userName>`     | Ubuntu ユーザーの既定の Bash を設定します。 指定されたユーザーが存在しない場合は、パスワードの入力が求められます。  詳細については、 https://aka.ms/wslusers をご覧ください。 <br/> **/y** を指定すると、パスワードの入力を求めるプロンプトは省略されます。  ユーザーはパスワードなしで作成されます。|
| `lxrun /update`            | サブシステムのパッケージ インデックスを更新します。          |
