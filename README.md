# s_js_scroll
ページ内スクロール、他ページからの推移にも対応

```
$(function(){
  // 全てのアンカータグを対象にする
  $('a').click(function(e){
    var anchor = $(this),
        href = anchor.attr('href'),
        pagename = window.location.href;
    // 現在のurlのハッシュ以降を削除
    pagename = pagename.replace(/#.*/,'');
    // リンク先のurlから現在の表示中のurlを削除
    href = href.replace( pagename , '' );
    if( href.search(/^#/) >= 0 ){
      // 整形したリンクがページ内リンクの場合はページ無いスクロールの対象とする
      // 通常の遷移処理をキャンセル
      e.preventDefault();
      var speed = 500;
      // 前段階で整形したhrefを使用する
      // var href= $(this).attr("href");
      var target = $(href == "#" || href == "" ? 'html' : href);
      var position = target.offset().top;
      $("html, body").animate({scrollTop:position}, speed, "swing");
      // ロケーションバーの内容を書き換え
      location.hash = href ;
      return false;
    }
  });
});

```

https://commono.jp/2017/11/22/how_to_adopt_smooth-scroll_to_full_path_url/
