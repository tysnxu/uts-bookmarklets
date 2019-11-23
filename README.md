# UTS Bookmarklets


吼吼 大家好！

给大家分享几个最近写的 JS Bookmarklet，
希望对大家在UTS各个系统的使用体验有点帮助。

-----------------------
# Slider Value Viewer

在 [UTS Review](https://uts.review-edu.com/uts/) 查分系统使用，
打开assessment详情页面运行。


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


-----------------------
# GPA Calculator

这个是在 [one stop admin](https://onestopadmin.uts.edu.au) 网站上用的，在results页面无需等待，一键算出GPA。

（仅对一直在UTS的成绩有效，对于Diploma转过来的成绩无效）

（未对挂科重修的成绩单做测试）

```
javascript:function E(){sub = document.getElementsByClassName("table table-bordered table-striped")[0].getElementsByTagName("tbody")[0].getElementsByTagName("tr");sub_n = sub.length;n = 0;f = 0;for (a=0;a<sub.length;a++){console.log("---------------");console.log(sub[a].getElementsByTagName("td")[3].innerText);g = sub[a].getElementsByTagName("td")[6].innerText;if (g == "Fail") {n = 0.5;console.log("Failed Assessment");} else {if (g == "Pass") {console.log("pass, 1.5");n = 1.5;} else if (g == "Credit") {console.log("Credit, 2.5");n = 2.5;} else if (g == "Distinction") {console.log("Distinction, 3.5");n = 3.5;} else if (g == "High Distinction") {console.log("HD, 4");n = 4;}};console.log(f + " + " + n + " = " + (f + n));f += n;};console.log("---------------");console.log("GPA: " + (f/sub_n).toFixed(2));alert("GPA: " + (f/sub_n).toFixed(2));} E()
```
