---
layout: default
title: 購入
---
Test

<form action="https://credit.j-payment.co.jp/gateway/payform.aspx" method="POST">
    <input type="hidden" name="aid" value="119743">
    <input type="hidden" name="pt" value="1">
    <input type="hidden" name="cmd" value="0">
    <input type="hidden" name="jb" value="CAPTURE">
    <input type="hidden" name="am" value="1000">
    <input type="hidden" name="tx" value="10">
    <input type="hidden" name="sf" value="0">
    <input type="submit" name="submit" value="購入">
</form>

<FORM ACTION="https://credit.j-payment.co.jp/gateway/payform.aspx" METHOD="POST">
    <INPUT TYPE="HIDDEN" NAME="aid" value="119743">
    <INPUT TYPE="HIDDEN" NAME="pt" VALUE="1">
    <INPUT TYPE="HIDDEN" NAME="iid" VALUE="003">
    <INPUT TYPE="submit" NAME="submit" VALUE="従量課金">
</FORM>
        
<form id="mainform">
    <input id="tkn" name="tkn" type="hidden" value="">
    <div id="CARD_INPUT_FORM"></div>
    <input type="button" value="購入する" onclick="doPurchase()"/>
</form>


<script type="text/javascript" src="https://credit.j-payment.co.jp/gateway/js/jquery.js"></script>
<script type="text/javascript" src="https://credit.j-payment.co.jp/gateway/js/CPToken.js"></script>
<script>
// カード情報入力フォーム表示
function doPurchase() {
    //CP非同期通信よりカード番号入力画面を表示する
    CPToken.CardInfo(
        {
            aid: '119743'
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
        $("#mainform").submit();
    }
}
</script>
    
