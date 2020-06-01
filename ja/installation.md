---
layout: content
title: Nuのインストール
prev: 開始
next: はじめに
link_prev: /ja/table_of_contents.html
link_next: /ja/introduction.html
---

今のところNuをインストールするもっともよい方法は、[crates.io](https://crates.io)からインストールするか、ビルド済のバイナリーを[リリースページ](https://github.com/nushell/nushell/releases)からダウンロードするか、ソースからビルドすることです。
Dockerを利用してビルド済のコンテナをプルしてくる方法もあります。

## ビルド済みのバイナリー

ビルド済のNuは[リリースページ](https://github.com/nushell/nushell/releases)からダウンロードできます。もし、macOSで[Homebrew](https://brew.sh/) を利用しているなら、`brew install nushell`を実行して、バイナリーをインストールできます。

## Windows

**Note** NuはWindows 10で動作しますが、現在のところ7/8.1のサポートはありません。

[リリースページ](https://github.com/nushell/nushell/releases)から`.zip`ファイルをダウンロードして、例えば次の箇所に解凍します。

{% include installation/windows_example_extraction_location.md %}

そして、`nu`フォルダをPATHに追加します。これが済めば、`nu`コマンドでNuを起動できます。

{% include installation/windows_run_nu.md %}

もし、[Windows Terminal](https://github.com/microsoft/terminal)を使っているなら、次のようにして`nu`をデフォルトシェルに指定できます。

{% include installation/windows_terminal_default_shell.md %}

この設定をTerminal Settingsの`"profiles"`に追加します。そして、`"defaultProfile"`を次のように変更します。

{% include installation/windows_change_default_profile.md %}

これで`nu`がWindows Terminalの起動時にロードされます。

## ビルド済のDockerコンテナ

ビルド済のDockerコンテナをプルしたい場合はQuay.io上で[nushell organization](https://quay.io/organization/nushell)のためのタグを閲覧できます。
コンテナのプルは以下のように行います。

{% include installation/pull_prebuilt_container.md %}

"nu-base"と"nu"のどちらにもバイナリーが含まれますが、nu-baseには`/code`内にソースコードと全ての依存関係も含まれています。

[dockerfiles](https://github.com/nushell/nushell/tree/master/docker)を利用してローカルにコンテナをビルドすることもできます。
ベースイメージをビルドするには:

{% include installation/build_containers_locally_base_image.md %}

そして、小さなコンテナをビルドするには(マルチステージビルドを利用):

{% include installation/build_containers_locally_multistage_build.md %}

どちらの方法でも、次のようにコンテナを実行できます:

{% include installation/run_containers_built_locally.md %}

サイズを重要視する場合は、２番目のコンテナのほうが少し小さくなります。

## 事前準備

Nuをインストールする前に、システムに必要なツールがそろっているか確認する必要があります。現在、Rustのツールチェインといくつかの依存関係が必要です。

### コンパイラスイートのインストール

Rustが適切に機能するには、互換性のあるコンパイラスイートがシステムにインストールされている必要があります。推奨されるコンパイラスイートは次のとおりです。

* Linux: GCC or Clang
* macOS: Clang (install Xcode)
* Windows: [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)

LinuxとmacOSの場合、コンパイラのインストールが完了すれば、`rustup`でのRustのインストールの準備が整います。

Windowsの場合、Visual Studio Community Editionをインストールするときに、「C ++ビルドツール」をインストールする必要があります。
オプショナルなインストールとして提供されている`link.exe`が必要なためです。これで次のステップに進む準備ができました。

### Rustのインストール

Rustがシステムにまだインストールされていない場合は、[rustup](https://rustup.rs/)を利用してRustをインストールする方法がベストです。Rustupは、異なるRustのバージョンのインストールを管理するツールです。

Nuは現在、**最新のstable(1.39 or later)** バージョンのRustを必要とします。
`rustup`で正しいversionを選択するのが良い方法です。
最初に"rustup"を実行すると、インストールするRustのバージョンを尋ねられます。

{% include installation/rustup_choose_rust_version.md %}

準備ができたら、1を押してからエンターを押します。

もし、`rustup`を経由してRustをインストールしたくない場合、他の方法でもインストールすることができます。(例えば、Linuxディストリビューションのパッケージから)
その場合でもRustの1.39以上のバージョンがインストールされるようにしてください。
## 依存関係

### Debian / Ubuntu

"pkg-config"および"libssl-dev"パッケージをインストールしてください。

{% include installation/install_pkg_config_libssl_dev.md %}

`rawkey`や`clipboard`機能を使用するLinuxユーザーは"libx11-dev"および"libxcb-composite0-dev"パッケージをインストールする必要があります。

{% include installation/use_rawkey_and_clipboard.md %}

### macOS

[Homebrew](https://brew.sh/)を利用して、"openssl"と"cmake"をインストールしてください。

{% include installation/macos_deps.md %}

## [crates.io](https://crates.io)からのインストール

必要となる依存関係が準備できたら、Rustコンパイラーに付属している`cargo`を使って、Nuをインストールできます。

{% include installation/cargo_install_nu.md %}

これでおしまいです！`cargo`はNuのソースコードとその依存関係をダウンロードしてビルドし、`cargo`のバイナリーパスにインストールすることでNuを実行できるようにします。

より多くの機能をインストールするには、次のようにします。

{% include installation/cargo_install_nu_more_features.md %}

すべての機能を利用するための最も簡単な方法はNuをチェックアウトして、Rustツールを利用してビルドすることです。

{% include installation/build_nu_yourself.md %}

インストールが完了すると、`nu`コマンドでNuを実行できます。

{% include installation/crates_run_nu.md %}

## ソースからビルド

githubのソースから直接ビルドすることもできます。こうすることで、最新の機能やバグ修正にすぐにアクセスすることができます。

{% include installation/git_clone_nu.md %}

Gitでメインのnushellリポジトリをクローンし、Nuをビルドして実行できます。

{% include installation/build_nu_from_source.md %}

リリースモードでNuをビルドし実行することもできます。

{% include installation/build_nu_from_source_release.md %}

## ログインシェルとして設定するには

**!!! Nuは開発中なので、日常使いのシェルとしての安定性を欠く可能性があります!!!**

[`chsh`](https://linux.die.net/man/1/chsh)コマンドを使用して、ログインシェルを設定できます。
一部のLinuxディストリビューションには`/etc/shells`に有効なシェルのリストが記載されており、Nuがホワイトリストに登録されるまで変更ができません。
`shells`ファイルを更新していない場合は次のようなエラーが表示される場合があります。

{% include installation/chsh_invalid_shell_error.md %}

Nuバイナリを`shells`ファイルに追加することにより、許可されたシェルのリストにNuを追加できます。
追加するパスは`which nu`コマンドで見つけることができます。通常は`$HOME/.cargo/bin/nu`です。
