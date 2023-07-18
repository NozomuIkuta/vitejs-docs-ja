# プロジェクト理念

## 無駄のない拡張可能なコア

Vite は、すべてのユーザーのすべてのユースケースをカバーするつもりはありません。Vite は、Web アプリケーションを構築するための最も一般的なパターンをすぐにサポートすることを目指していますが、プロジェクトの長期的な保守性を維持するために、[Vite のコア](https://github.com/vitejs/vite)は小さな API サーフェスで無駄のない状態を維持しなければなりません。この目標は、[Vite の Rollup ベースのプラグインシステム](./api-plugin.md)のおかげで可能になりました。外部プラグインとして実装できる機能は、一般的に Vite コアには追加されません。[vite-plugin-pwa](https://vite-pwa-org.netlify.app/) は Vite コアで実現できることの素晴らしい例であり、あなたのニーズをカバーする[よく整備されたプラグイン](https://github.com/vitejs/awesome-vite#plugins)がたくさんあります。Vite は Rollup プロジェクトと密接に協力し、Plugin API に必要な拡張を可能な限り上流にプッシュすることで、plain-rollup と Vite の両方のプロジェクトでプラグインが可能な限り使用できるようにしています。

## モダン Web を推し進める

Vite は、モダンなコードを書くことを後押しする opinionated な機能を提供します。例:

- ソースコードは ESM でのみ書くことができます。ESM 以外の依存関係を動作させるには [ESM として事前にバンドル](./dep-pre-bundling) する必要があります。
- Web ワーカーは最新の標準に従うため、[`new Worker` 構文](./features#web-workers) で書くことが推奨されます。
- Node.js モジュールはブラウザでは使用できません。

新しい機能を追加する際には、これらのパターンに従って将来性のある API を作成します。それは他のビルドツールと互換性があるとは限りません。

## パフォーマンスへの実用的なアプローチ

Vite はその[始まり](./why.md)以来、パフォーマンスに重点を置いてきました。その開発サーバーアーキテクチャは、プロジェクトの規模が大きくなっても高速なまま維持する HMR を可能にします。Vite は [esbuild](https://esbuild.github.io/) や [SWC](https://github.com/vitejs/vite-plugin-react-swc) のようなネイティブツールを使って集中的なタスクを実装しますが、スピードと柔軟性のバランスを取るために残りのコードは JS に保持します。必要に応じて、フレームワークのプラグインはユーザーコードをコンパイルするために [Babel](https://babeljs.io/) を利用します。そしてビルド時に Vite は現在 [Rollup](https://rollupjs.org/) を使用しています。バンドルサイズやプラグインの幅広いエコシステムにアクセスすることが単純なスピードよりも重要です。Vite は、API の安定性を保ちつつ、DX を向上させる新しいライブラリが登場すればそれを使用し、内部的に進化し続けます。

## Vite 上にフレームワークを構築する

Vite はユーザーが直接使用することもできますが、フレームワークを作成するためのツールとして輝いています。Vite のコアはフレームワークに依存しませんが、各 UI フレームワーク用に洗練されたプラグインが用意されています。その [JS API](./api-javascript.md) によって、アプリフレームワークの作者は Vite の機能を使ってユーザーに合わせた体験を作ることができます。Vite は [SSR プリミティブ](./ssr.md)のサポートを含んでいます。これは通常、より高いレベルのツールに存在しますが、モダンな Web フレームワークを構築するための基本です。また、Vite プラグインは、フレームワーク間で共有する方法を提供することで、全体像を完成させます。Vite はまた、[Ruby](https://vite-ruby.netlify.app/) や [Laravel](https://laravel.com/docs/10.x/vite) のような[バックエンドフレームワーク](./backend-integration.md)と組み合わせるときにも最適です。

## アクティブなエコシステム

Vite の進化は、フレームワークやプラグインのメンテナ、ユーザ、そして Vite チームの協力によって成り立っています。プロジェクトが Vite を採用したら、Vite のコア開発に積極的に参加することを推奨しています。[vite-ecosystem-ci](https://github.com/vitejs/vite-ecosystem-ci) のようなツールに助けられながら、各リリースでのリグレッションを最小化するために、エコシステムの主要なプロジェクトと密接に協力しています。このツールにより、選択した PR に対して Vite を使用して主要プロジェクトの CI を実行することができ、エコシステムがリリースに対してどのように反応するかを明確に把握することができます。私たちは、ユーザーに影響を与える前にリグレッションを修正し、プロジェクトがリリースされたらすぐに次のバージョンにアップデートできるように努めています。もしあなたが Vite で仕事をしているのであれば、ぜひ [Vite の Discord](https://chat.vitejs.dev) に参加して、プロジェクトにも参加してください。