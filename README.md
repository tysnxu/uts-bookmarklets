# Review Edu Bookmarklets

吼吼 大家好！

给大家分享一个最近写的 JS Bookmarklet，
希望对大家UTS Review的使用体验有点帮助。

-----------------------

仅显示当前Assessment的真实得分：

```
javascript:function E(){g = document.getElementsByClassName("ui-slider-handle ui-state-default handle-main handle-main-staff ui-corner-all");alert(g[g.length - 1].style.cssText.slice(6, -1))} E()
```

根据百分比计算出这个section的总分：
```
javascript:function E(){g = document.getElementsByClassName("ui-slider-handle ui-state-default handle-main handle-main-staff ui-corner-all");gn = g[g.length - 1].style.cssText.slice(6, -2);id = document.getElementsByClassName("legend-tab btn btn-mini btn-print pull-right pdf_download_btn")[0]["href"].slice(-18).replace(/\D/g,'');sel_id = document.getElementsByClassName("span8")[0].getElementsByTagName('select')[3].getElementsByTagName('option');for (a = 0; a < sel_id.length; a++ ) {num_sel = sel_id[a]["value"];if (num_sel == id) {p = sel_id[a].innerHTML.slice(-5).replace(/[{(%)}]/g, '')}};pn = Number("0." + p);alert("Your Final Grade: " + gn + " * " + p + "% = " + (Number(gn)*pn).toFixed(2));} E()
```

列出当前Assessment 所有criteria值的：
```
javascript:function E(){g = document.getElementsByClassName("ui-slider-handle ui-state-default handle-main handle-main-staff ui-corner-all");var d = "Grade Info: \n\n";for (a = 0; a < (g.length-1); a++) { w = document.getElementsByClassName("margin10-t margin10-b")[a].innerText.replace(/\D/g,'')+"%"; d += "Criteria " + (a+1) + " : "+ g[a].style.cssText.slice(6, -2) + " * " + w + "\n"};d += "Final: "+g[g.length - 1].style.cssText.slice(6, -1);alert(d);} E()
```
