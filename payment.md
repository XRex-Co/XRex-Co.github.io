---
layout: default
title: 購入
---
Test

<form action="https://credit.j-payment.co.jp/gateway/payform.aspx" method="POST">
    <input type="hidden" name="aid" value="119747">
    <input type="hidden" name="pt" value="1">
    <input type="hidden" name="cmd" value="0">
    <input type="hidden" name="jb" value="CAPTURE">
    <input type="hidden" name="am" value="1000">
    <input type="hidden" name="tx" value="100">
    <input type="hidden" name="sf" value="0">
    <input type="submit" name="submit" value="購入">
</form>

<FORM ACTION="https://credit.j-payment.co.jp/gateway/payform.aspx" METHOD="POST">
    <INPUT TYPE="HIDDEN" NAME="aid" value="119747">
    <INPUT TYPE="HIDDEN" NAME="pt" VALUE="1">
    <INPUT TYPE="HIDDEN" NAME="iid" VALUE="003">
    <INPUT TYPE="submit" NAME="submit" VALUE="従量課金">
</FORM>
        
<form id="popup">
    <input id="tkn" name="tkn" type="hidden" value="">
    <input id="aid" name="aid" type="hidden" value="119747">
    <input id="jb" name="jb" type="hidden" value="CAPTURE">
    <input id="rt" name="rt" type="hidden" value="1">
    <input id="cod" name="cod" type="hidden" value="001">
    <input id="pn" name="pn" type="hidden" value="0300000000">
    <input id="em" name="em" type="hidden" value="ksuke@outlook.jp">
    <input id="am" name="am" type="hidden" value="100">
    <input id="tx" name="tx" type="hidden" value="10">
    <input id="sf" name="sf" type="hidden" value="0">
    <div id="CARD_INPUT_FORM"></div>
    <input type="button" value="ポップアップ方式" onclick="doPurchase()"/>
</form>

<form id="customize">
カード番号：<input type="text" value="" name="cn" id="cn" /><br/>
カード有効期限：<input type="text" value="" name="ed_year" id="ed_year" /> /<input type="text" value="" name="ed_month" id="ed_month" /><br/>
カード名義人：<input type="text" value="" name="fn" id="fn" /><input type="text" value="" name="ln" id="ln" /><br/>
<input id="tkn" name="tkn" type="hidden" value="">
<input type="button" value="購入する" onclick="doPurchaseCustomize()"/>
</form>

<script type="text/javascript" src="https://credit.j-payment.co.jp/gateway/js/jquery.js"></script>
<script type="text/javascript" src="https://credit.j-payment.co.jp/gateway/js/CPToken.js"></script>
<script>
// カード情報入力フォーム表示
function doPurchase() {
    //CP非同期通信よりカード番号入力画面を表示する
    CPToken.CardInfo(
        {
            aid: '119747'
        },
        execPurchase
    );
}
// コールバック関数
function execPurchase(resultCode, errMsg) {
    if (resultCode != "Success") {
        // 戻り値がSuccess以外の場合はエラーメッセージを表示
        window.alert(errMsg);
    } else {
        // スクリプトからフォームをsubmit
        $("#popup").submit();
    }
}
    
function doPurchaseCustomize() {
    // CP非同期通信よりトークンを生成する
    CPToken.TokenCreate(
        {
            aid: '119747',
            cn: $("#cn").val(),
            ed: $("#ed_year").val() + $("#ed_month").val(),
            fn: $("#fn").val(),
            ln: $("#ln").val()
        },
        execPurchaseCustomize
    );
}
// コールバック関数
function execPurchaseCustomize(resultCode, errMsg) {
    if (resultCode != "Success") {
        window.alert(errMsg);
    } else {
        // カード情報を消去
        $("#cn").val("");
        $("#ed_year").val("");
        $("#ed_month").val("");
        $("#fn").val("");
        $("#ln").val("");
        //スクリプトからフォームをsubmit
        $("#mainform").submit();
    }
}
</script>
    
