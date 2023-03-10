var CookiedAjax = [];
function addEvent(e, t, a) {
  e.addEventListener ? e.addEventListener(t, a, false) : e.attachEvent && e.attachEvent("on" + t, a);
}
function Begin() {
  MainRightBar = false, MainRightBarAll = false, $(".Items--Slider--Grid").length > 0 && $(".Items--Slider--Grid").owlCarousel({loop: false, rtl: true, nav: true, dots: true, autoWidth: true, margin: 16, smartSpeed: 250, navText: ["<a class='Slides-prev'><i class='fal fa-angle-left'></i></a>", "<a class='Slides-next'><i class='fal fa-angle-right'></i></a>"]}), $(".PhotosListSlides").length > 0 && $(".PhotosListSlides").owlCarousel({loop: false, rtl: true, nav: true, dots: true, autoWidth: true, margin: 16, smartSpeed: 350, navText: ["<a class='Slides-prev'><i class='fal fa-angle-left'></i></a>", "<a class='Slides-next'><i class='fal fa-angle-right'></i></a>"]}).on("changed.owl.carousel", function () {
    setTimeout(function () {
      CurrItem = $(".PhotosList .owl-stage-outer .owl-item.active"), $(".bg--singlecontainerright > span").attr("style", "background-image:url(" + CurrItem.find("img").attr("src") + ");");
    }, 50);
  }), $("singlecontainer").length > 0 ? ($("messengerbutton").hide(), $("messenger").hide()) : ($("messengerbutton").show(), $("messenger").show());
}
function getTime(e) {
  var t = e % 60 ? e % 60 : "00";
  t = Math.trunc(t);
  var a = Math.floor(e / 60);
  return (a = Math.trunc(a)) + ":" + t;
}
function getSeconds(e) {
  var t = e % 60 ? e % 60 : "00";
  return t = Math.trunc(t);
}
function getMinutes(e) {
  var t = Math.floor(e / 60);
  return t = Math.trunc(t);
}
String.prototype.hasBG = function () {
  var e, t = false, a = this, o = (a = (a = $("<b>" + a + "</b>").text()).replace(EmojiRegexp, "☺")).split(" ");
  return $.each(o, function (a) {
    "☺" == (e = o[a]) || !$.trim(e) || (t = true);
  }), t;
}, $(window).on("load", function () {
  $("filterloadshere").length > 0 && $.ajax({url: HomeURL + "/AjaxCenter/RightBar/", dataType: "json", type: "GET", success: function (e) {
    $("filterloadshere").after(e.output).remove();
  }});
}), Begin();
var players = [], playersids = [], ReleasePlayer = function (e) {
  $("trailerbox").each(function (t, a) {
    0 == $(a).find("paused--trailer-box").length && $(a).data("id") != e && ($(a).hide(), $(a).html('<player id="player' + $(a).data("id") + '"></player>'));
  });
};
if ($("body").on("click", ".login--now", function () {
  return data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login"), e.preventDefault(), false;
}), $("body").on("click", "add_to_watchlist", function () {
  var e = $(this), t = "post", a = e.data("post");
  return 0 == Currentuser_Logged || (AjaxURL = HomeURL + "/AjaxCenter/UserSubmissions/AddToWatchlist/", null != e.data("term") && (t = "term", a = e.data("term")), $.ajax({url: AjaxURL, dataType: "json", data: {user: Currentuser_ID, type: t, id: a}, type: "POST", success: function (t) {
    e.after(t.output).remove();
  }})), false;
}), $("body").on("click", ".trailer--post-item", function () {
  ReleasePlayer(), TrailerBoxButton = $(this), TrailerBox = $(this).parent().parent().find("trailerbox"), TrailerBox.find(".loader").remove(), TrailerBox.show(), TrailerBox.append('<div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div>'), players[TrailerBoxButton.data("id")] = new YT.Player("player" + TrailerBoxButton.data("id"), {playerVars: {autoplay: 1, loop: 1, controls: 1, showinfo: 0, autohide: 1, modestbranding: 1, vq: "hd1080"}, height: TrailerBox.height(), width: TrailerBox.width(), videoId: TrailerBoxButton.data("url"), events: {onReady: function () {}, onStateChange: function (e) {
    switch (e.data) {
      case 0:
        $(".paused--trailer-box").remove(), $(".WatchShowNow--paused--trailer-box").remove(), TrailerBox.hide(), TrailerBox.html('<player id="player' + TrailerBoxButton.data("id") + '"></player>'), playersids.splice(TrailerBoxButton.data("id"));
        break;
      case 1:
        $(".paused--trailer-box").remove(), $(".WatchShowNow--paused--trailer-box").remove(), playersids.push(TrailerBoxButton.data("id"));
        break;
      case 2:
        var t, a, o, i, s;
        a = (o = players[TrailerBoxButton.data("id")]).getDuration() - o.getCurrentTime(), minutes = getMinutes(a), 1 == (i = getSeconds(a)) ? strseconds = "<em>ثانية واحدة</em>" : 2 == i ? strseconds = "<em>ثانيتان</em>" : i > 2 && (strseconds = i > 10 ? "<em>" + i + "</em> ثانية" : "<em>" + i + "</em> ثواني"), 1 == minutes ? strminutes = "<em>دقيقة واحدة</em>" : 2 == minutes ? strminutes = "<em>دقيقتان</em>" : minutes > 2 && (strminutes = "<em>" + minutes + "</em> دقائق"), t = "متبقي : ", i > 0 && minutes > 0 ? t += strminutes + " و " + strseconds : minutes > 0 ? t += strminutes : t += i > 0 ? i > 25 && i < 35 ? "<em>نصف دقيقة</em>" : strseconds : "<em>ثانية واحدة</em>", s = '<div class="paused--trailer-box">', s += '<div class="bg--paused--trailer-box"></div>', s += '<div class="poster--paused--trailer-box" style="background-image:url(' + TrailerBoxButton.data("poster") + ');"></div>', s += '<div class="icon--paused--trailer-box">', s += '<i class="fas fa-play"></i><time>' + t + "</time>", s += "</div>", s += "</div>", s += '<a class="WatchShowNow--paused--trailer-box hoverable activable" href="' + TrailerBoxButton.data("watch") + '">مشاهدة الآن <i class="fal fa-chevron-left"></i></a>', TrailerBox.append(s), playersids.splice(TrailerBoxButton.data("id"));
    }
  }}});
}), $("body").on("click", ".paused--trailer-box", function () {
  var e = $(this).parent().data("id");
  ReleasePlayer(e), players[e].playVideo();
}), $("body").on("click", ".PostItemMoreButton", function () {
  var e = $(this);
  return e.parent().find(".Ellipsis").remove(), e.hide(), e.before('<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>'), AjaxSystem = $.ajax({url: HomeURL + "/AjaxCenter/MoreInfoPost/" + $(this).data("info") + "/", dataType: "json", success: function (t) {
    e.parent().find(".showbox").remove(), e.before(t.content), e.remove();
  }}), false;
}), $("body").on("click", ".GotoTop", function () {
  $("body, html").animate({scrollTop: 0}, 200);
}), $(window).scroll(function () {
  $(window).scrollTop() > 50 && $(".GotoTop").addClass("visible"), $(window).scrollTop() < 50 && $(".GotoTop").removeClass("visible");
}), $("wecimabegin-inner").length > 0) {
  var AddedVisible = false;
  $(window).scroll(function () {
    $(window).scrollTop() > 60 & 0 == AddedVisible && ($("header").addClass("visible"), AddedVisible = true), $(window).scrollTop() < 60 & 1 == AddedVisible && ($("header").removeClass("visible"), AddedVisible = false);
  }), $(window).scrollTop() > 60 && ($("header").addClass("visible"), AddedVisible = true), $(window).scrollTop() < 60 && ($("header").removeClass("visible"), AddedVisible = false);
} else $("header").addClass("visible"), AddedVisible = true;
var RetryInterval, AjaxHandlerXHR = false;
function AjaxRequest(e) {
  return 0 != AjaxHandlerXHR && AjaxHandlerXHR.abort(), e.error = function (t, a) {
    var o = "";
    404 == t.status ? (o = "لم يتم العثور على الصفحة.", AjaxHandlerXHR = false) : 500 == t.status ? (o = "حدث خطأ اثناء معاينة الملف.", AjaxHandlerXHR = false) : "timeout" === a && (o = "إنتهت مهلة الإتصال.", AjaxHandlerXHR = false), "" != o && null != o && (RetryInterval = setInterval(AjaxRequest(e), 5e3));
  }, AjaxHandlerXHR = $.ajax(e).done(function () {
    clearInterval(RetryInterval), AjaxHandlerXHR = false, InitializeTrig();
  }), true;
}
var LazyloadOffset = 0;
function Lazyload() {
  $("[data-lazy-style]").each(function (e, t) {
    var a = $(t).offset().top - $(window).height();
    $(window).scrollTop() >= a && ($(t).attr("style", $(t).attr("data-lazy-style")), $(t).removeAttr("data-lazy-style"));
  }), $("[data-lazy-src]").each(function (e, t) {
    var a = $(t).offset().top - $(window).height();
    $(window).scrollTop() >= a && ($(t).attr("src", $(t).attr("data-lazy-src")), $(t).removeAttr("data-lazy-src"));
  }), $("[data-lazy-href]").each(function (e, t) {
    var a = $(t).offset().top - $(window).height();
    $(window).scrollTop() >= a && ($(t).attr("href", $(t).attr("data-lazy-href")), $(t).removeAttr("data-lazy-href"));
  });
}
setInterval(function () {
  $(".owl-item.active [data-owl-img]").each(function (e, t) {
    OffsetTop = $(t).offset().top, WindowSTop + WindowHeight > OffsetTop && $(t).attr("style", $(this).attr("data-owl-img")).removeAttr("data-owl-img");
  });
}, 1e3);
var Lazyloaded = false;
function InitializeTrig() {
  0 == Lazyloaded && AjaxRequest({url: HomeURL + "/insights.php", dataType: "json", type: "POST", data: {cheking: true}, success: function (e) {
    if (Lazyloaded = true, 0 == e.isPageSpeed) {
      function t() {
        dataLayer.push(arguments);
      }
      Lazyload(), $(window).on("load", Lazyload), $(window).on("resize", Lazyload), $(window).scroll(Lazyload), $(".RightUI").scroll(Lazyload), $(".LeftUI").scroll(Lazyload), $(".WatchServers > ul li:first-child > btn").trigger("click"), window.dataLayer = window.dataLayer || [], t("js", new Date), t("config", "UA-128370636-1");
    }
  }});
}
InitializeTrig();
var HometabsLoadingAjaxXHR, SearchingTimeout, HometabsLoadingNow = false;
$("body").on("click", "wecimabegin-inner ul.tabs > li", function () {
  $(this).parent().find("li.selected").removeClass("selected").addClass("hoverable"), $(this).addClass("selected").removeClass("hoverable"), 1 == HometabsLoadingNow && HometabsLoadingAjaxXHR.abort(), HometabsLoadingNow = true;
  var e = HomeURL + "/AjaxCenter/HomeTabs/" + $(this).data("tab") + "/";
  HometabsLoadingAjaxXHR = $.ajax({url: e, dataType: "json", success: function (e) {
    $("tab--wecimabegin-inner").html(e.output), HometabsLoadingNow = false, Begin();
  }});
}), $("body").on("click", ".WatchServers > ul li > btn", function () {
  var e = $(this);
  if (e.parent().parent().parent().find("li").removeClass("selected"), e.parent().addClass("selected"), "" != e.data("url") && null != e.data("url")) {
    var t = '<iframe name="watch" src="' + e.data("url") + '" src="" id="IframeEmbed" height="100%" width="100%" allowfullscreen frameborder="0" scrolling="no"></iframe>';
    t += '<div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div>', $(".Inner--WatchServersEmbed").html(t);
  } else {
    t = '<a href="' + e.data("player") + '" target="_blank" class="player-app"><player-app-inner><i class="fa fa-play"></i><p>أنقر هنا للإنتقال لصفحة المشاهدة</p></player-app-inner></a>';
    $(".Inner--WatchServersEmbed").html(t);
  }
}), $("body").on("click", ".MoreEpisodes--Button", function () {
  var e = $(this);
  e.addClass("loading");
  var t = HomeURL + "/AjaxCenter/MoreEpisodes/" + e.data("term") + "/" + $(".Episodes--Seasons--Episodes > a").length + "/";
  $.ajax({url: t, dataType: "json", success: function (t) {
    $(".Episodes--Seasons--Episodes").append(t.output), e.removeClass("loading");
  }});
}), $(".pagination > ul > li > a").addClass("hoverable activable"), $("header > middle--header > ul > li.menu-item-has-children > a").append('<i class="fal fa-angle-left"></i>'), $("header > middle--header > ul > li > a").addClass("activable"), $("header > middle--header > ul > li a").addClass("hoverable"), $("header > middle--header > ul > li.current-menu-item > a i.fal").length > 0 && $("header > middle--header > ul > li.current-menu-item > a i.fal").attr("class", $("header > middle--header > ul > li.current-menu-item > a i.fal").attr("class").replace("fal", "fas")), $("body").on("click", "productionslistbutton", function () {
  $(this).parent().toggleClass("open");
}), $("body").on("click", ".Close--SearchingBox", function () {
  $(".Searching--Overlay > form-search > input").val(""), $(".Searching--Overlay > form-search > .Close--SearchingBox").remove();
  var e = $(".search--userarea--rightbar").clone();
  $(e).prependTo(".userarea--rightbar"), $(".Searching--Overlay").remove(), LastWord = "";
});
var SearchingAjaxXHR, FBOpen, FBOpenInterval, SearchingCanAjax = true, LastWord = "";
function Responsivness() {
  $(document).width() < 1260 ? (0 == $("singlecontainer > singlecontainerleft").length && $(".LeftUI").hide(), $(".LeftUI").addClass("ToggledSide"), $('.options--leftside-user > a > i[data-popover="user--settings"]').after('<i data-sidebar="leftbar" class="hoverable activable fas fa-bars"></i>'), $('.options--leftside-user > a > i[data-popover="user--settings"]').remove()) : (0 == $("singlecontainer > singlecontainerleft").length && $(".LeftUI").show(), $(".LeftUI").removeClass("ToggledSide"), $('.options--leftside-user > a > i[data-sidebar="leftbar"]').after('<i data-popover="user--settings" class="hoverable activable fas fa-caret-down"></i>'), $('.options--leftside-user > a > i[data-sidebar="leftbar"]').remove()), $(document).width() < 1140 ? 0 == $(".Button--Menubar--UX").length && ($("middle--header").prepend('<div class="Button--Menubar--UX"><span class="hoverable activable"><i class="fa fa-caret-down"></i> تصفح الأقسام</span></div>'), $("header > middle--header > ul").appendTo(".Button--Menubar--UX"), $("middle--header").addClass("Menubar--UX")) : $(".Button--Menubar--UX").length > 0 && ($(".Button--Menubar--UX > .NavigationMenu").prependTo("middle--header"), $("middle--header").removeClass("Menubar--UX"), $(".Button--Menubar--UX").remove()), $(document).width() < 1130 ? ($(".RightUI").hasClass("opened") || $(".RightUI").hide(), 0 == $(".RightSideFlex .RightSideFlex--Openmenu").length && $(".RightSideFlex").prepend('<div class="RightSideFlex--Openmenu hoverable activable"><i class="far fa-ellipsis-h"></i></div>')) : ($(".RightUI").show(), $(".RightSideFlex .RightSideFlex--Openmenu").length > 0 && $(".RightSideFlex .RightSideFlex--Openmenu").remove()), $(document).width() < 740 ? $("middle--header > .ProductionsListButton").appendTo(".Button--Menubar--UX > .NavigationMenu") : $(".Button--Menubar--UX > .NavigationMenu > .ProductionsListButton").appendTo("middle--header"), $(document).width() < 650 ? ($("singlecontainer > singlecontainerleft").appendTo("singlesections"), $("header").addClass("double--header")) : ($("singlesections > singlecontainerleft").appendTo("singlecontainer"), $("header").removeClass("double--header")), $(".GridItem .react-area--social").removeClass("FromLeft"), $(".GridItem").each(function (e, t) {
    OffsetLeft = $(t).offset().left, OffsetLeft < 180 && $(t).find(".react-area--social").addClass("FromLeft");
  });
}
$("body").on("keyup keydown keypress", ".search--userarea--rightbar > input", function (e) {
  var t = $(".search--userarea--rightbar > input").val();
  0 == $(".Results--Searching--Overlay > .circular").length && t != LastWord && $(".Results--Searching--Overlay").html('<svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg>'), clearTimeout(SearchingTimeout), 0 == SearchingCanAjax && SearchingAjaxXHR.abort(), SearchingTimeout = setTimeout(function () {
    if ((t = $(".search--userarea--rightbar > input").val()) != LastWord) {
      var e = HomeURL + "/AjaxCenter/Searching/" + t + "/";
      SearchingCanAjax = false, LastWord = t, SearchingAjaxXHR = $.ajax({url: e, dataType: "json", success: function (e) {
        $(".Results--Searching--Overlay").html(e.output), SearchingCanAjax = true;
      }});
    }
  }, 500);
}), $("body").on("keydown", ".search--userarea--rightbar > input", function (e) {
  if (0 == $(".Searching--Overlay").length) {
    var t = $(".search--userarea--rightbar").clone();
    $(".search--userarea--rightbar").remove(), '<div class="Searching--Overlay">', '<div class="Results--Searching--Overlay">', "</div>", "</div>", $('<div class="Searching--Overlay"><div class="Results--Searching--Overlay"></div></div>').appendTo("body"), $(t).prependTo(".Searching--Overlay"), $(".Searching--Overlay > form-search").append('<div class="Close--SearchingBox hoverable activable"><i class="fal fa-times"></i></div>'), $(".search--userarea--rightbar > input").focus();
  }
}), $("body").on("click", ".LoginButton", function () {
  return data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login"), false;
}), $("body").on("click", ".Button--Menubar--UX > .NavigationMenu > li.menu-item-has-children > a", function () {
  return $(this).parent().toggleClass("open"), false;
}), $("body").on("click", ".RightSideFlex--Openmenu", function () {
  $(".RightUI").toggleClass("opened"), $(".RightUI").toggle(), $(".RightUI").hasClass("opened") ? ($(".RightSideFlex--Openmenu > i").attr("class", "fas fa-times"), $("body").append('<div class="Wecima--overlay"></div>')) : ($(".RightSideFlex--Openmenu > i").attr("class", "fas fa-ellipsis-h"), $(".Wecima--overlay").remove()), $("filterloadshere").length > 0 && $.ajax({url: HomeURL + "/AjaxCenter/RightBar/", dataType: "json", type: "POST", success: function (e) {
    $("filterloadshere").after(e.output).remove();
  }});
}), $("body").on("click", ".Button--Menubar--UX > span", function () {
  $(this).parent().toggleClass("open");
}), $("body").on("click", '[data-sidebar="leftbar"]', function () {
  return $(".LeftUI").toggleClass("opened"), $(".LeftUI").toggle(), $(".LeftUI").hasClass("opened") ? ($('[data-sidebar="leftbar"]').attr("class", "fal fa-times hoverable activable"), $("body").append('<div class="Wecima--overlay"></div>')) : ($('[data-sidebar="leftbar"]').attr("class", "fas fa-bars hoverable activable"), $(".Wecima--overlay").remove()), false;
}), $(document).mouseup(function (e) {
  var t;
  $(".LeftUI.opened").length > 0 && ((t = $('.LeftUI, .options--leftside-user > a > i[data-sidebar="leftbar"]')).is(e.target) || 0 !== t.has(e.target).length || $('.options--leftside-user > a > i[data-sidebar="leftbar"]').trigger("click"));
  ((t = $(".Button--Menubar--UX")).is(e.target) || 0 !== t.has(e.target).length || t.removeClass("open"), $(".RightUI.opened").length > 0) && ((t = $(".RightUI, .RightSideFlex--Openmenu")).is(e.target) || 0 !== t.has(e.target).length || $(".RightSideFlex--Openmenu").trigger("click"));
}), $(window).on("resize", function () {
  Responsivness();
}), $(document).ready(function () {
  Responsivness();
}), $(window).on("load", function () {
  Responsivness();
}), Responsivness(), $("body").on("click", ".facebook--buttons-collection", function () {
  var e, t;
  width = 800, url = $(this).attr("href"), height = 500, e = window.screen.width / 2 - (width / 2 + 10), t = window.screen.height / 2 - (height / 2 + 50), FBOpen = window.open(url, "FBOpen", "status=no,height=" + height + ",width=" + width + ",resizable=yes,left=" + e + ",top=" + t + ",screenX=" + e + ",screenY=" + t + ",toolbar=no,menubar=no,scrollbars=no,location=no,directories=no");
  var a = setInterval(function () {
    if (FBOpen.closed) {
      $(".inner--Context---overlays").append('<div class="loader--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div>'), $(".inner--Context---overlays > form").addClass("Checking");
      var e = (new Date).valueOf();
      $.ajax({url: HomeURL + "/AjaxCenter/isLogged/", dataType: "json", type: "POST", data: {time: e}, success: function (e) {
        1 == e.logged ? ($(".loader--Context---overlays").html('<i class="fas fa-check-circle"></i>'), location.reload()) : ($(".loader--Context---overlays").addClass("Error").html('<i class="fas fa-times-circle"></i><p>حدث خطأ اثناء تسجيل الدخول</p>'), setTimeout(function () {
          $(".loader--Context---overlays").remove(), $(".inner--Context---overlays > form").removeClass("Checking");
        }, 1e3));
      }}), clearTimeout(a);
    }
  }, 500);
  return false;
}), $("body").on("click", ".signup--buttons-collection", function () {
  return data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Signup"), false;
}), $("body").on("click", ".login--buttons-collection", function () {
  return data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login"), false;
});
var Base64 = {_keyStr: "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/=", encode: function (e) {
  var t, a, o, i, s, n, r, l = "", d = 0;
  for (e = Base64._utf8_encode(e); d < e.length;) i = (t = e.charCodeAt(d++)) >> 2, s = (3 & t) << 4 | (a = e.charCodeAt(d++)) >> 4, n = (15 & a) << 2 | (o = e.charCodeAt(d++)) >> 6, r = 63 & o, isNaN(a) ? n = r = 64 : isNaN(o) && (r = 64), l = l + this._keyStr.charAt(i) + this._keyStr.charAt(s) + this._keyStr.charAt(n) + this._keyStr.charAt(r);
  return l;
}, decode: function (e) {
  var t, a, o, i, s, n, r = "", l = 0;
  for (e = e.replace(/[^A-Za-z0-9\+\/\=]/g, ""); l < e.length;) t = this._keyStr.indexOf(e.charAt(l++)) << 2 | (i = this._keyStr.indexOf(e.charAt(l++))) >> 4, a = (15 & i) << 4 | (s = this._keyStr.indexOf(e.charAt(l++))) >> 2, o = (3 & s) << 6 | (n = this._keyStr.indexOf(e.charAt(l++))), r += String.fromCharCode(t), 64 != s && (r += String.fromCharCode(a)), 64 != n && (r += String.fromCharCode(o));
  return r = Base64._utf8_decode(r);
}, _utf8_encode: function (e) {
  e = e.replace(/\r\n/g, "\n");
  for (var t = "", a = 0; a < e.length; a++) {
    var o = e.charCodeAt(a);
    o < 128 ? t += String.fromCharCode(o) : o > 127 && o < 2048 ? (t += String.fromCharCode(o >> 6 | 192), t += String.fromCharCode(63 & o | 128)) : (t += String.fromCharCode(o >> 12 | 224), t += String.fromCharCode(o >> 6 & 63 | 128), t += String.fromCharCode(63 & o | 128));
  }
  return t;
}, _utf8_decode: function (e) {
  for (var t = "", a = 0, o = c1 = c2 = 0; a < e.length;) (o = e.charCodeAt(a)) < 128 ? (t += String.fromCharCode(o), a++) : o > 191 && o < 224 ? (c2 = e.charCodeAt(a + 1), t += String.fromCharCode((31 & o) << 6 | 63 & c2), a += 2) : (c2 = e.charCodeAt(a + 1), c3 = e.charCodeAt(a + 2), t += String.fromCharCode((15 & o) << 12 | (63 & c2) << 6 | 63 & c3), a += 3);
  return t;
}}, removeElements = function (e, t) {
  var a = $("<span>" + e + "</span>");
  return a.find(t).remove(), a.html();
};
function placeCaretAtEnd(e) {
  if (e.focus(), void 0 !== window.getSelection && void 0 !== document.createRange) {
    var t = document.createRange();
    t.selectNodeContents(e), t.collapse(false);
    var a = window.getSelection();
    a.removeAllRanges(), a.addRange(t);
  } else if (void 0 !== document.body.createTextRange) {
    var o = document.body.createTextRange();
    o.moveToElementText(e), o.collapse(false), o.select();
  }
}
function stripHTML(e) {
  var t = document.createElement("div"), a = document.createTextNode(e);
  return t.appendChild(a), t.innerHTML;
}
function CleanPastedHTML(e) {
  var t = e.replace(/(\n|\r| class=(")?Mso[a-zA-Z]+(")?)/g, " "), a = new RegExp("<!--(.*?)-->", "g"), o = (t = t.replace(a, ""), new RegExp("<(/)*(meta|link|span|\\?xml:|st1:|o:|font)(.*?)>", "gi"));
  t = t.replace(o, "");
  for (var i = ["style", "script", "applet", "embed", "noframes", "noscript"], s = 0; s < i.length; s++) o = new RegExp("<" + i[s] + ".*?" + i[s] + "(.*?)>", "gi"), t = t.replace(o, "");
  var n = ["style", "start"];
  for (s = 0; s < n.length; s++) {
    var r = new RegExp(" " + n[s] + '="(.*?)"', "gi");
    t = t.replace(r, "");
  }
  return t;
}
function pasteHtmlAtCaret(e) {
  var t, a;
  if (window.getSelection) {
    if ((t = window.getSelection()).getRangeAt && t.rangeCount) {
      (a = t.getRangeAt(0)).deleteContents();
      var o = document.createElement("div");
      o.innerHTML = e;
      for (var i, s, n = document.createDocumentFragment(); i = o.firstChild;) s = n.appendChild(i);
      a.insertNode(n), s && ((a = a.cloneRange()).setStartAfter(s), a.collapse(true), t.removeAllRanges(), t.addRange(a));
    }
  } else document.selection && "Control" != document.selection.type && document.selection.createRange().pasteHTML(e);
}
var charstoformid = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXTZabcdefghiklmnopqrstuvwxyz".split(""), UniqID = function () {
  for (var e = "", t = 0; t < 10; t++) e += charstoformid[Math.floor(Math.random() * charstoformid.length)];
  return e;
}, ReactionsScrollingAjax = true, NotFoundReacts = false, LoadingItems = '<li class="LoadingItem"><div class="avatar--loading"><span></span></div><div class="title--loading"></div><div class="request--loading"></div></li><li class="LoadingItem"><div class="avatar--loading"><span></span></div><div class="title--loading"></div><div class="request--loading"></div></li><li class="LoadingItem"><div class="avatar--loading"><span></span></div><div class="title--loading"></div><div class="request--loading"></div></li>', ReactionsScrolling = function () {
  if ($(this).scrollTop() > $(".reactions--list").height() - $(this).height() - 100 && 1 == ReactionsScrollingAjax && 0 == NotFoundReacts) {
    ReactionsScrollingAjax = false;
    var e = $("div.parent--reactions--list li.ReactItem");
    AjaxURL = ReactionsURL + ReactionsCurrentTab + "/" + e.length + "/", $(".reactions--list").append(LoadingItems), ReactionsTimoutAjax = $.ajax({url: AjaxURL, dataType: "json", success: function (e) {
      $("div.parent--reactions--list li.LoadingItem").remove(), !$.trim(e.output) ? (ReactionsScrollingAjax = true, NotFoundReacts = true) : ($(".reactions--list").append(e.output), ReactionsScrollingAjax = true);
    }});
  }
};
function ReactionsFormat() {
  MaxWidth = 472;
  var e = $(".title--Context---overlays ul.reactions--tabs li").length, t = false;
  $(".title--Context---overlays ul.reactions--tabs li").each(function (a, o) {
    Element = $(".title--Context---overlays ul.reactions--tabs > li:nth-child(" + e + ")"), e -= 1, $(".reactions--tabs").width() > MaxWidth && ($(Element).hide().addClass("minireact"), t = true);
  }), 1 == t && ($(".title--Context---overlays ul.reactions--tabs").append('<li data-tab="more" data-live="true" class="hoverable">المزيد <i class="fas fa-caret-down"></i></li>'), 0 == $("ul.reactions--tabs .parent--popover").length && (PopoverElem = '<div class="parent--popover minipopover" style="display:none;">', PopoverElem += '<div class="inner--parent---popover withouticons"></div>', PopoverElem += "</div>", $(".title--Context---overlays ul.reactions--tabs").append(PopoverElem), $(".title--Context---overlays ul.reactions--tabs li.minireact").each(function (e, t) {
    $(t).show().clone().appendTo("ul.reactions--tabs .inner--parent---popover"), $(t).remove();
  })));
}
function HideParentPopover(e, t) {
  null != t ? $(".parent--popover").not($(t)).hide() : $(".parent--popover").hide(), null != e ? $("[data-popover]").not(e).removeClass("open") : $("[data-popover]").removeClass("open");
}
var ReactionsTimoutAjax, PhotoEnabled = false, ReactionsTimout = true, ReactionsCurrentTab = "all";
function Window(e, t, a) {
  var o, i;
  o = window.screen.width / 2 - (t / 2 + 10), i = window.screen.height / 2 - (a / 2 + 50), window.open(e, "Window2", "status=no,height=" + a + ",width=" + t + ",resizable=yes,left=" + o + ",top=" + i + ",screenX=" + o + ",screenY=" + i + ",toolbar=no,menubar=no,scrollbars=no,location=no,directories=no");
}
$("body").on("click", ".title--Context---overlays ul.reactions--tabs li[data-tab]", function () {
  var e = $(this);
  "more" == e.data("tab") ? e.parent().find(".parent--popover").toggle() : (HideParentPopover(), $(".title--Context---overlays ul.reactions--tabs li").removeClass("selected").addClass("hoverable"), e.addClass("selected").removeClass("hoverable"), $('.title--Context---overlays ul.reactions--tabs li[data-tab="more"]').removeClass("selected"), $(".parent--reactions--list").html('<div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div>'), 0 == ReactionsTimout && ReactionsTimoutAjax.abort(), ReactionsTimout = false, ReactionsURL = ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = ReactionsURL.replace("/all", "")).replace("/love", "")).replace("/haha", "")).replace("/sad", "")).replace("/like", "")).replace("/angry", "")).replace("/wow", ""), AjaxURL = ReactionsURL + e.data("tab") + "/", ReactionsTimoutAjax = $.ajax({url: AjaxURL, dataType: "json", success: function (t) {
    ReactionsCurrentTab = e.data("tab"), NotFoundReacts = false, $(".parent--reactions--list").after(t.output).remove(), $(".parent--reactions--list").scroll(ReactionsScrolling);
  }}));
}), $("body").on("click", ".title--Context---overlays ul.reactions--tabs .parent--popover li[data-tab]", function () {
  $('.title--Context---overlays ul.reactions--tabs li[data-tab="more"]').addClass("selected");
});
var OverlayAjaxInit, OverlayAjax = true;
function Context(e, t, a) {
  /*var o, i;
  "overlay" == e && (1 != t.confirmation ? (CloseOverlay(true), Overlay = '<div class="Context--overlays loading">') : ($(".Context--overlays.confirmationbox").remove(), Overlay = '<div class="Context--overlays confirmationbox loading">'), Overlay += '<div class="Backdrop--Context---overlays"></div>', Overlay += "Addpost" == a ? '<div class="OverParent-Boxed--Context---overlays addpost--overparent">' : '<div class="OverParent-Boxed--Context---overlays">', Overlay += '<div class="Parent-Boxed--Context---overlays">', Overlay += '<div class="Boxed--Context---overlays">', Overlay += '<div class="title--Context---overlays">', Overlay += t.title, Overlay += '<span class="Close--title---Context----overlays activable"><i class="fas fa-times"></i></span>', Overlay += "</div>", Overlay += '<div class="inner--Context---overlays">', Overlay += t.content, Overlay += "</div>", Overlay += "</div>", Overlay += "</div>", Overlay += "</div>", Overlay += "</div>", 0 == $(".Context--overlays.confirmationbox").length && ($("body").append(Overlay), $("body").addClass("disablescrolling")), 1 == t.ajax && (0 == OverlayAjax && OverlayAjaxInit.abort(), null != t.args && (i = t.args), OverlayAjax = false, null != t.folder ? (o = HomeURL + "/AjaxCenter/" + t.folder + "/" + a + "/", OverlayAjaxInit = $.ajax({url: o, dataType: "json", data: {user: Currentuser_ID, args: i}, type: "POST", success: function (e) {
    OverlayAjax = true, null != e.title && (Title = e.title, Title += '<span class="Close--title---Context----overlays activable"><i class="fas fa-times"></i></span>', $(".title--Context---overlays").html(Title)), $(".Context--overlays").removeClass("loading"), $(".inner--Context---overlays").html(e.output), $(".inner--Context---overlays [autofocus]").focus(), null != t.fastimage ? FileChangeListener($(t.fastimage.eleme), t.fastimage.data) : null != t.fasttool && $('[data-posttools="' + t.fasttool + '"]').trigger("click");
  }})) : (o = HomeURL + "/AjaxCenter/" + a + "/", OverlayAjaxInit = $.ajax({url: o, dataType: "json", success: function (e) {
    OverlayAjax = true, Title = e.title, Title += '<span class="Close--title---Context----overlays activable"><i class="fas fa-times"></i></span>', $(".Context--overlays").removeClass("loading"), $(".inner--Context---overlays").html(e.output), $(".title--Context---overlays").html(Title), $(".inner--Context---overlays [autofocus]").focus();
  }}))));*/
}
function Confirmation(e, t) {
  "cover-upload" == e && (ConfirmBox = "<confirmation>", ConfirmBox += '<span><i class="fas fa-globe-americas"></i> تظهر صورة غلافك للعامة.</span>', ConfirmBox += "<ul>", ConfirmBox += '<li class="hoverable activable close" data-action="deny" data-cover="' + t.id + '" data-submission="cover">إلغاء</li>', ConfirmBox += '<li class="hoverable activable confirm" data-action="confirm" data-cover="' + t.id + '" data-submission="cover">حفظ التغييرات</li>', ConfirmBox += "</ul>", ConfirmBox += "</confirmation>", $("body").append(ConfirmBox));
}
function CloseOverlay(e) {
  e ? ($(".Context--overlays").remove(), $("body").removeClass("disablescrolling")) : CloseOverlay(true);
}
$("body").on("click", ".Context--overlays:not(.confirmationbox) .Backdrop--Context---overlays", function () {
  CloseOverlay();
}), $("body").on("click", ".Context--overlays.confirmationbox .Backdrop--Context---overlays", function () {
  $(this).parent().remove(), $("body").removeClass("disablescrolling");
}), $("body").on("click", ".Close--title---Context----overlays", function () {
  $(this).parent().parent().parent().parent().parent().remove();
});
var ReactionsURL = void 0;
$("body").on("click", "[data-button]:not(a), a.readmore--comment-item, a.reply--actions---post", function () {
  var e = $(this);
  if (HideParentPopover(), "addcomment" == e.data("button")) Elem = $('.addcomment-input--post[data-post="' + e.data("post") + '"]'), Elem.parent().parent().parent().show(), Elem.parent().parent().show(), $('.post-comments--postitem[data-post="' + e.data("post") + '"]').show(), Elem.focus(); else if ("readmore-comment" == e.data("button")) e.css({"pointer-events": "none"}), e.append('<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>'), AjaxSystem = $.ajax({url: HomeURL + "/AjaxCenter/CommentContent/" + $(this).data("comment") + "/", dataType: "json", success: function (t) {
    e.css({"pointer-events": "inherit"}), e.parent().html(t.content), e.find(".showbox").remove();
  }}); else if ("mention" == e.data("button")) data = {title: "<strong>إنشاء منشور</strong>", fasttool: "mention", args: {cat: $("addpost").data("cat")}, ajax: true, folder: "UserActions", content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Addpost"); else if ("feeling" == e.data("button")) data = {title: "<strong>إنشاء منشور</strong>", fasttool: "feeling", args: {cat: $("addpost").data("cat")}, ajax: true, folder: "UserActions", content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Addpost"); else if ("replycomment" == e.data("button")) null != e.data("reply") && (e = $('.reply--actions---post[data-comment="' + e.data("reply") + '"]')), ReplyBox = '<div class="ReplyBox">', ReplyBox += '<div class="AddComment">', ReplyBox += '<div class="AddCommentAvatar">', ReplyBox += Currentuser_Avatar, ReplyBox += "</div>", ReplyBox += '<div class="AddCommentInput">', ReplyBox += '<div type="text" data-post="' + e.parent().parent().parent().parent().data("post") + '" data-comment="' + e.data("comment") + '" data-type="reply" class="addcomment-input--post" contenteditable="true" role="textbox" spellcheck="true"></div>', ReplyBox += '<span class="placeholder">كتابة رد ...</span>', ReplyBox += '<div class="AddCommentEmotes">', ReplyBox += '<div class="photo--comment" data-field="upload-photo--reply-comment" data-action="upload-input"><i class="fal fa-camera"></i></div>', ReplyBox += '<div class="emotions--comment"><i class="fal fa-smile"></i></div>', ReplyBox += "</div>", ReplyBox += "</div>", ReplyBox += "</div>", ReplyBox += "</div>", e.parent().parent().find(".ReplyBox").length > 0 ? e.parent().parent().find(".ReplyBox").toggle() : e.parent().parent().find(".more--post-comments---postitem").length > 0 ? e.parent().parent().find(".more--post-comments---postitem").after(ReplyBox) : e.parent().parent().find(".reply--comment").after(ReplyBox), e.parent().parent().find(".ReplyBox .addcomment-input--post").focus(); else if ("reactions" == e.data("button")) {
    $(".Context--overlays.confirmationbox").remove(), a = '<div class="Context--overlays confirmationbox loading">', a += '<div class="Backdrop--Context---overlays"></div>', a += '<div class="OverParent-Boxed--Context---overlays">', a += '<div class="Parent-Boxed--Context---overlays">', a += '<div class="Boxed--Context---overlays">', a += '<div class="title--Context---overlays">', a += "<loader></loader>", a += '<span class="Close--title---Context----overlays activable"><i class="fas fa-times"></i></span>', a += "</div>", a += '<div class="inner--Context---overlays">', a += '<div class="Loading--Context---overlays"><em></em><em></em></div>', a += "</div>", a += "</div>", a += "</div>", a += "</div>", a += "</div>", $("body").append(a), $("body").addClass("disablescrolling"), 0 == OverlayAjax && OverlayAjaxInit.abort(), OverlayAjax = false, null != e.data("react") ? (ReactionsCurrentTab = e.data("react"), t = HomeURL + "/AjaxCenter/PostReactions/" + e.data("type") + "/" + e.data("post") + "/" + e.data("react") + "/") : (ReactionsCurrentTab = "all", t = HomeURL + "/AjaxCenter/PostReactions/" + e.data("type") + "/" + e.data("post") + "/all/"), ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = (ReactionsURL = t.replace("/all", "")).replace("/all", "")).replace("/love", "")).replace("/haha", "")).replace("/sad", "")).replace("/like", "")).replace("/angry", "")).replace("/wow", ""), OverlayAjaxInit = $.ajax({url: t, dataType: "json", success: function (e) {
      OverlayAjax = true, Title = e.title, Title += '<span class="Close--title---Context----overlays activable"><i class="fas fa-times"></i></span>', $(".Context--overlays").removeClass("loading"), $(".inner--Context---overlays").html(e.output), $(".title--Context---overlays").html(Title), $(".inner--Context---overlays [autofocus]").focus(), ReactionsFormat(), NotFoundReacts = false, $(".parent--reactions--list").scroll(ReactionsScrolling);
    }});
  } else if ("mentions" == e.data("button")) {
    var t, a;
    $(".Context--overlays.confirmationbox").remove(), a = '<div class="Context--overlays confirmationbox loading">', a += '<div class="Backdrop--Context---overlays"></div>', a += '<div class="OverParent-Boxed--Context---overlays">', a += '<div class="Parent-Boxed--Context---overlays">', a += '<div class="Boxed--Context---overlays">', a += '<div class="title--Context---overlays">', a += "<loader></loader>", a += '<span class="Close--title---Context----overlays activable"><i class="fas fa-times"></i></span>', a += "</div>", a += '<div class="inner--Context---overlays">', a += '<div class="Loading--Context---overlays"><em></em><em></em></div>', a += "</div>", a += "</div>", a += "</div>", a += "</div>", a += "</div>", $("body").append(a), $("body").addClass("disablescrolling"), 0 == OverlayAjax && OverlayAjaxInit.abort(), OverlayAjax = false, t = HomeURL + "/AjaxCenter/PostMentions/" + e.data("post") + "/", OverlayAjaxInit = $.ajax({url: t, dataType: "json", success: function (e) {
      OverlayAjax = true, Title = e.title, Title += '<span class="Close--title---Context----overlays activable"><i class="fas fa-times"></i></span>', $(".Context--overlays").removeClass("loading"), $(".inner--Context---overlays").html(e.output), $(".title--Context---overlays").html(Title), $(".inner--Context---overlays [autofocus]").focus(), ReactionsFormat();
    }});
  } else "readmore-timelinepost" == e.data("button") && (e.css({"pointer-events": "none"}), e.append('<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>'), AjaxSystem = $.ajax({url: HomeURL + "/AjaxCenter/PostContent/" + $(this).data("post") + "/", dataType: "json", success: function (t) {
    e.css({"pointer-events": "inherit"}), e.parent().html(t.content), e.find(".showbox").remove();
  }}));
  return false;
});
var TooltipAbort, TooltipAjax = true;
$("body").on("mouseover", "[data-button]", function (e) {
  var t = $(this);
  if ("react" == t.data("button")) ReactButtons = '<div class="emoji  emoji--like" data-action="react" data-type="' + t.find(".InnerButton").data("type") + '" data-post="' + t.data("post") + '" data-react="like" data-tooltip="أعجبني">', ReactButtons += '<div class="emoji__hand">', ReactButtons += '<div class="emoji__thumb"></div>', ReactButtons += "</div>", ReactButtons += "</div>", ReactButtons += '<div class="emoji  emoji--love" data-action="react" data-type="' + t.find(".InnerButton").data("type") + '" data-post="' + t.data("post") + '" data-react="love" data-tooltip="أحببته">', ReactButtons += '<div class="emoji__heart"></div>', ReactButtons += "</div>", ReactButtons += '<div class="emoji  emoji--haha" data-action="react" data-type="' + t.find(".InnerButton").data("type") + '" data-post="' + t.data("post") + '" data-react="haha" data-tooltip="هاهاها">', ReactButtons += '<div class="emoji__face">', ReactButtons += '<div class="emoji__eyes"></div>', ReactButtons += '<div class="emoji__mouth">', ReactButtons += '<div class="emoji__tongue"></div>', ReactButtons += "</div>", ReactButtons += "</div>", ReactButtons += "</div>", ReactButtons += '<div class="emoji  emoji--wow" data-action="react" data-type="' + t.find(".InnerButton").data("type") + '" data-post="' + t.data("post") + '" data-react="wow" data-tooltip="واااو">', ReactButtons += '<div class="emoji__face">', ReactButtons += '<div class="emoji__eyebrows"></div>', ReactButtons += '<div class="emoji__eyes"></div>', ReactButtons += '<div class="emoji__mouth"></div>', ReactButtons += "</div>", ReactButtons += "</div>", ReactButtons += '<div class="emoji  emoji--sad" data-action="react" data-type="' + t.find(".InnerButton").data("type") + '" data-post="' + t.data("post") + '" data-react="sad" data-tooltip="أحزنني">', ReactButtons += '<div class="emoji__face">', ReactButtons += '<div class="emoji__eyebrows"></div>', ReactButtons += '<div class="emoji__eyes"></div>', ReactButtons += '<div class="emoji__mouth"></div>', ReactButtons += "</div>", ReactButtons += "</div>", ReactButtons += '<div class="emoji  emoji--angry" data-action="react" data-type="' + t.find(".InnerButton").data("type") + '" data-post="' + t.data("post") + '" data-react="angry" data-tooltip="أغضبني">', ReactButtons += '<div class="emoji__face">', ReactButtons += '<div class="emoji__eyebrows"></div>', ReactButtons += '<div class="emoji__eyes"></div>', ReactButtons += '<div class="emoji__mouth"></div>', ReactButtons += "</div>", ReactButtons += "</div>", t.find(".react-area--social").removeClass("close").removeAttr("style"), "" == t.find(".react-area--social").html() && ($(".react-area--social").html(""), t.find(".react-area--social").html(ReactButtons)); else if ("reactions" == t.data("button")) {
    if (0 == ISMobile) if (0 == t.find("tooltip").length) 0 == TooltipAjax && TooltipAbort.abort(), TooltipAjax = false, $("body > tooltip").remove(), Hash = UniqID(), a = t.offset().top + t.height(), leftorig = t.offset().left, i = t.width() / 2, (o = leftorig + i - 32.5) < 0 && (o = 5), Tooltip = '<tooltip style="top:' + a + "px;left:" + o + 'px;" class="TooltipLoader-' + Hash + '">', null != t.data("tooltip-title") && (Tooltip += "<strong>" + t.data("tooltip-title") + "</strong>"), Tooltip += '<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>', Tooltip += "</tooltip>", AjaxURL = HomeURL + "/AjaxCenter/ReactionsList/" + t.data("type") + "/" + t.data("post") + "/", null != t.data("react") && (AjaxURL += t.data("react") + "/"), $("body").append(Tooltip), $("tooltip.TooltipLoader-" + Hash).fadeIn(200), null != CookiedAjax[AjaxURL] ? ($("tooltip.TooltipLoader-" + Hash).html(CookiedAjax[AjaxURL]), (o = leftorig + i - $("tooltip.TooltipLoader-" + Hash).width() / 2) < 0 && (o = 5), $("tooltip.TooltipLoader-" + Hash).attr("style", "top:" + a + "px;left:" + o + "px;display:block;"), TooltipAjax = true) : TooltipAbort = $.ajax({url: AjaxURL, dataType: "json", success: function (e) {
      TooltipAjax = true, !$.trim(e.output) ? $("tooltip.TooltipLoader-" + Hash).remove() : (CookiedAjax[AjaxURL] = e.output, $("tooltip.TooltipLoader-" + Hash).html(e.output), (o = leftorig + i - $("tooltip.TooltipLoader-" + Hash).width() / 2) < 0 && (o = 5), $("tooltip.TooltipLoader-" + Hash).attr("style", "top:" + a + "px;left:" + o + "px;display:block;"));
    }});
  } else if ("mentions" == t.data("button")) {
    var a, o, i;
    if (0 == t.find("tooltip").length) 0 == TooltipAjax && TooltipAbort.abort(), TooltipAjax = false, $("body > tooltip").remove(), Hash = UniqID(), a = t.offset().top + t.height(), leftorig = t.offset().left, i = t.width() / 2, (o = leftorig + i - 32.5) < 0 && (o = 5), Tooltip = '<tooltip style="top:' + a + "px;left:" + o + 'px;" class="TooltipLoader-' + Hash + '">', null != t.data("tooltip-title") && (Tooltip += "<strong>" + t.data("tooltip-title") + "</strong>"), Tooltip += '<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>', Tooltip += "</tooltip>", AjaxURL = HomeURL + "/AjaxCenter/MentionsList/" + t.data("post") + "/", $("body").append(Tooltip), $("tooltip.TooltipLoader-" + Hash).fadeIn(200), null != CookiedAjax[AjaxURL] ? ($("tooltip.TooltipLoader-" + Hash).html(CookiedAjax[AjaxURL]), (o = leftorig + i - $("tooltip.TooltipLoader-" + Hash).width() / 2) < 0 && (o = 5), $("tooltip.TooltipLoader-" + Hash).attr("style", "top:" + a + "px;left:" + o + "px;display:block;"), TooltipAjax = true) : TooltipAbort = $.ajax({url: AjaxURL, dataType: "json", success: function (e) {
      TooltipAjax = true, !$.trim(e.output) ? $("tooltip.TooltipLoader-" + Hash).remove() : (CookiedAjax[AjaxURL] = e.output, $("tooltip.TooltipLoader-" + Hash).html(e.output), (o = leftorig + i - $("tooltip.TooltipLoader-" + Hash).width() / 2) < 0 && (o = 5), $("tooltip.TooltipLoader-" + Hash).attr("style", "top:" + a + "px;left:" + o + "px;display:block;"));
    }});
  }
}), $("body").on("dragstart drop", function (e) {
  return e.preventDefault(), false;
}), $(document).mouseup(function (e) {
  var t;
  if ((t = $(".Results--Searching--Overlay, .Searching--Overlay > form-search")).is(e.target) || 0 !== t.has(e.target).length || $(".Close--SearchingBox").trigger("click"), (t = $("chat--tools")).is(e.target) || 0 !== t.has(e.target).length || t.hide(), (t = $(".ProductionsListButton")).is(e.target) || 0 !== t.has(e.target).length || t.removeClass("open"), (t = $("filterboxselection")).is(e.target) || 0 !== t.has(e.target).length || t.removeClass("open"), (t = $(".emoticons--box")).is(e.target) || 0 !== t.has(e.target).length || t.remove(), !(t = $(".emote--item--messages--chatitem, .actions--item--messages--chatitem")).is(e.target) && 0 === t.has(e.target).length) {
    var a = $(".chatitem--chatbody .tools--item--messages--chatitem.focused");
    a.is(e.target) || 0 !== a.has(e.target).length || ($(".chatitem--chatbody .tools--item--messages--chatitem.focused").removeClass("focused"), t.remove());
  }
  (t = $(".parent--popover, [data-popover]")).is(e.target) || 0 !== t.has(e.target).length || HideParentPopover(), (t = $(".Parent-Boxed--Context---overlays")).is(e.target) || 0 !== t.has(e.target).length || CloseOverlay(), moving = false;
}), $(document).mouseover(function (e) {
  var t;
  if ((t = $('[data-button="reactions"], [data-button="mentions"]')).is(e.target) || 0 !== t.has(e.target).length || (t.find("tooltip").remove(), 0 == TooltipAjax && TooltipAbort.abort()), !(t = $("tooltip")).is(e.target) && 0 === t.has(e.target).length) {
    var a = $('[data-button="reactions"]');
    if (!a.is(e.target) && 0 === a.has(e.target).length) {
      var o = $('[data-button="mentions"]');
      o.is(e.target) || 0 !== o.has(e.target).length || t.remove();
    }
  }
}), $("body").on("click", ".emoticons--box > .emoticons-bar--box > span", function (e) {
  $(".emoticons--box > .emoticons-bar--box > span").removeClass("selected"), $(this).addClass("selected"), ThisEL = $(this), ScrollHandler = 0, $('.emoticons-area--box > div[data-key="' + ThisEL.data("emojis") + '"]').prevAll().each(function (e, t) {
    ScrollHandler += $(t).height();
  }), $(".emoticons-area--box").animate({scrollTop: ScrollHandler}, 500);
});
var EmoticonsHandler = function () {
  setTimeout(function () {
    $(".emoticons-area--box").scroll(function () {
      ScrollMover = 0, $(".emoticons-area--box > div").each(function (e, t) {
        $(".emoticons-area--box").scrollTop() + $(".emoticons-area--box").height() >= ScrollMover && ($(".emoticons--box > .emoticons-bar--box > span").removeClass("selected"), $('.emoticons--box > .emoticons-bar--box > span[data-emojis="' + $(t).data("key") + '"]').addClass("selected"), 1 != $(t).data("added") && (EmotesBox = "", $.each(Emojis[$(t).data("key")], function (e, t) {
          EmotesBox += "<li>", EmotesBox += '<img alt="' + t.alt + '" src="' + t.src + '" />', EmotesBox += "</li>";
        }), $(t).find(".emoticons-list--box").html(EmotesBox), $(t).data("added", true))), ScrollMover = Number(ScrollMover + $(t).height());
      });
    });
  }, 200);
};
function AddNewComment(e) {
  $(e).find("*").not("emoji").length > 0 && ($(e).html(""), $(e).parent().find("span.placeholder").fadeIn(0));
  var t = $(e).html().replace(/^\s*[\r\n]/gm, "").replace(/\n/g, "<br/>"), a = $(e);
  if ((!!$.trim(t) || null != a.data("img") && 0 != a.data("img")) && 1 == Currentuser_Logged) {
    Hash = UniqID(), CommentItem = '<li class="just-now--comment" data-hash="' + Hash + '">', CommentItem += '<div class="comment-avatar--comments">' + Currentuser_Avatar + "</div>", !$.trim(t) ? CommentItem += '<div class="comment-area--comments emptycontent">' : CommentItem += '<div class="comment-area--comments">', CommentItem += '<div class="inner--comment-area---comments">', CommentItem += '<div class="bg--inner--comment-area---comments">', CommentItem += "<span>" + Currentuser_display_name + "</span>", CommentItem += '<p class="comment-area--content---comments">' + t + "</p>", CommentItem += "</div>", null != a.data("img") && 0 != a.data("img") && (CommentItem += '<div class="photos--comment">', CommentItem += '<div class="parent-item--photos--comment">', CommentItem += '<a href="#" class="item--photos--comment">', CommentItem += '<img src="' + a.data("img") + '" />', CommentItem += '<div class="loader--item--photos--comment">', CommentItem += '<svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg>', CommentItem += "</div>", CommentItem += "</a>", CommentItem += "</div>", CommentItem += "</div>"), CommentItem += "</div>", CommentItem += '<div class="actions--comment-area---comments">', CommentItem += '<a href="#" class="like--actions---post">أعجبني</a>', CommentItem += '<span aria-hidden="true" class="nbsp">&nbsp;·&nbsp;</span>', CommentItem += '<a href="#" class="reply--actions---post">رد</a>', CommentItem += '<span aria-hidden="true" class="nbsp">&nbsp;·&nbsp;</span>', CommentItem += '<time href="#" class="time--actions---post">دقيقة واحدة</time>', CommentItem += "</div>", CommentItem += "</div>", CommentItem += '<input id="Focusing" style="opacity:0;" />', CommentItem += "</li>", null == a.data("type") || "post" == a.data("type") || "series" == a.data("type") ? (CommentsArea = $('.post-comments--postitem[data-post="' + a.data("post") + '"]')).find("ul:not([data-comment])").append(CommentItem) : "reply" == a.data("type") && (CommentsArea = $('.reply--comment[data-comment="' + a.data("comment") + '"]')).append(CommentItem), CommentsArea.closest("singlecontainerleft").length > 0 && ($("#Focusing").focus(), $("#Focusing").remove(), a.focus()), null == a.data("type") || "post" == a.data("type") || "series" == a.data("type") ? AjaxURL = HomeURL + "/AjaxCenter/AddComment/" + a.data("type") + "/" + a.data("post") + "/" : "reply" == a.data("type") && (AjaxURL = HomeURL + "/AjaxCenter/AddComment/comment/" + a.data("post") + "/" + a.data("comment") + "/");
    var o = {comment: t, userID: Currentuser_ID, hash: Hash};
    null != a.data("img") && null != a.data("img") && (o.photo = a.data("img")), $.ajax({url: AjaxURL, dataType: "json", type: "POST", data: o, success: function (e) {
      $('[data-hash="' + Hash + '"]').after(e.comment), $('[data-hash="' + Hash + '"]').remove(), MoreButtonItem = a.parent().parent().parent().parent().find(".more--post-comments---postitem"), MoreButtonItem.data("offset", Number(MoreButtonItem.data("offset") + 1)), null != e.notify1 && (JSONData = {channel: "User@" + e.notify1.receiver, executed: {id: e.notify1.id, output: e.notify1.output, count: e.notify1.count}, type: "notification"}, PushTiming("notify", JSONData)), null != e.notify2 && (JSONData = {channel: "User@" + e.notify2.receiver, executed: {id: e.notify2.id, output: e.notify2.output, count: e.notify2.count}, type: "notification"}, PushTiming("notify", JSONData)), e.notify_mentioned.length > 0 && $.each(e.notify_mentioned, function (e, t) {
        JSONData = {channel: "User@" + t.receiver, executed: {id: t.id, output: t.output, count: t.count}, type: "notification"}, PushTiming("notify", JSONData);
      });
    }}), t = "", a.parent().find("span.placeholder").fadeIn(0), a.html(""), a.parent().parent().parent().find(".comm--previewphoto").remove(), a.data("img", false);
  }
}
function isBase64(e) {
  try {
    return btoa(atob(e)) == e;
  } catch (e) {
    return false;
  }
}
function FileChangeListener(e, t) {
  var a, o, i, s = e.attr("id"), n = new Image;
  n.src = t, n.onerror = function () {
    i = '<div class="DeletionAlert">', i += "<p>", i += "تعذر تحميل صورك. يجب أن يكون حجم الصور أقل من 4 ميجابايت ومحفوظة بتنسيق JPG أو PNG أو TIFF أو HEIF أو WebP.", i += "</p>", i += '<ul class="DeletionAlert--buttons">', i += '<li class="close--confirmation activable hoverable" data-self="third" data-confirmation="false">حسناََ</li>', i += "</ul>", Context("overlay", t = {title: "<strong>خطأ غير متوقع!</strong>", ajax: false, confirmation: true, content: i += "</div>"}, false), $('input[type="file"]').val(""), PostUploadingPhoto = "";
  }, n.onload = function () {
    if (this.width >= 200) if ("cover-upload" == s) $("innerpaddingauthorcover").append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UploadValidate/", dataType: "json", type: "POST", async: true, data: {file: t, folder: "covers", type: "image", user: Currentuser_ID}, success: function (e) {
      $("parentinnercover > blurred").html('<img src="' + e.blur + '" />'), $("innerpaddingauthorcover .cover--contain").addClass("positioning"), $("innerpaddingauthorcover .cover--contain img").length > 0 ? ($("innerpaddingauthorcover .cover--contain img").removeAttr("style"), $("innerpaddingauthorcover .cover--contain img").attr({src: e.image, id: e.id})) : $("innerpaddingauthorcover .cover--contain").append('<img class="cover--src" src="' + e.image + '" id="' + e.id + '" />'), $(".LoaderBoxed--Context---overlays").remove(), $(".profilesettings--cover").hide(), Confirmation(s, e);
    }}); else if ("profile-picture" == s) $(".Boxed--Context---overlays").append('<div class="LoaderBoxed--Context---overlays light"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UploadValidate/", dataType: "json", type: "POST", async: true, data: {file: t, folder: "avatars", type: "image", user: Currentuser_ID}, success: function (e) {
      $(".LoaderBoxed--Context---overlays").remove(), PhotoItem = '<li class="hoverable">', PhotoItem += '<a href="#" data-action="profilepicture--set" data-photo="' + e.id + '">', PhotoItem += '<span style="background-image:url(' + e.url + ');" />', PhotoItem += "</a>", PhotoItem += "</li>", $('.item--grid--photoslibrary[data-photos="avatars"] > ul').prepend(PhotoItem), $('[data-action="profilepicture--set"][data-photo="' + e.id + '"]').trigger("click");
    }}); else if ("upload-post-photo" == s) {
      var n;
      n = '<div class="SelectedPhotoItem">', n += '<img src="' + t + '" />', n += '<span class="Remove-SelectedPhotoItem hoverable activable"><i class="fal fa-times"></i></span>', n += "</div>", $(".scroll--addpost--context").addClass("HasImage"), $(".photo-preview--addpost--context").html(n), setTimeout(function () {
        $(".addpost-input--context").attr("style", "max-height:calc(100vh - 350px - " + $(".SelectedPhotoItem img").height() + "px);");
      }, 200), $(".addpost-input--context").addClass("SmallerText"), $(".addpost-input--context").find("emoji").attr("class", "emoji--global---wecima s20"), PhotoEnabled = true, PostUploadingPhoto = t, CanSavePost();
    } else "prepare-post-photo" == s ? (Context("overlay", t = {title: "<strong>إنشاء منشور</strong>", fastimage: {eleme: "#upload-post-photo", data: t}, args: {cat: $("addpost").data("cat")}, ajax: true, folder: "UserActions", content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, "Addpost"), PhotoEnabled = true) : "upload-chat-photo" == s ? UploadChatPhoto(e, t) : "upload-photo--comment" == s ? (Buttonelem = $('.focused[data-action="upload-input"]'), a = Buttonelem.parent().parent().parent(), a.find(".addcomment-input--post").data("post"), a.find(".addcomment-input--post").data("img", t), o = '<div class="comm--previewphoto">', o += '<img src="' + t + '" />', o += '<span class="remove--comm--previewphoto hoverable activable"><i class="fal fa-times"></i></span>', o += "</div>", a.append(o)) : "upload-photo--reply-comment" == s && (Buttonelem = $('.focused[data-action="upload-input"]'), a = Buttonelem.parent().parent().parent(), a.find(".addcomment-input--post").data("post"), a.find(".addcomment-input--post").data("img", t), o = '<div class="comm--previewphoto">', o += '<img src="' + t + '" />', o += '<span class="remove--comm--previewphoto hoverable activable"><i class="fal fa-times"></i></span>', o += "</div>", a.append(o)); else i = '<div class="DeletionAlert">', i += "<p>", i += "تعذر تحميل صورك. يجب أن يكون حجم الصور أقل من 4 ميجابايت ومحفوظة بتنسيق JPG أو PNG أو TIFF أو HEIF أو WebP.", i += "</p>", i += '<ul class="DeletionAlert--buttons">', i += '<li class="close--confirmation activable hoverable" data-self="third" data-confirmation="false">حسناََ</li>', i += "</ul>", Context("overlay", t = {title: "<strong>خطأ غير متوقع!</strong>", ajax: false, confirmation: true, content: i += "</div>"}, false), $('input[type="file"]').val(""), PostUploadingPhoto = "";
  };
}
$("body").on("click", ".emotions--comment", EmoticonsHandler), $("body").on("click", ".emotions--comment", function (e) {
  var t, a;
  $(this).parent().parent().find(".addcomment-input--post").length > 0 ? (EmotesBox = '<div class="emoticons--box">', t = "html") : $(this).parent().parent().find(".input--editor--chatinput").length > 0 ? (EmotesBox = '<div class="emoticons--box">', t = "chat") : (4, (a = $(".addpost--context").height() + $(".user--addpost---context").height() + 32 + $(".title--Context---overlays").height() - 370) < 370 ? (a = $(".addpost--context").height() + $(".user--addpost---context").height() + 32 + $(".title--Context---overlays").height() + 12, EmotesBox = '<div class="emoticons--box post--triggered-emotes down" style="top:' + a + 'px;left:4px;">') : EmotesBox = '<div class="emoticons--box post--triggered-emotes" style="top:' + a + 'px;left:4px;">', t = "append"), EmotesBox += '<div class="emoticons-area--box">', EmotesBox += '<div data-key="smiles" data-added="true">', EmotesBox += "<span>رموز تعبيرية وأشخاص</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.smiles, function (e, t) {
    EmotesBox += "<li>", EmotesBox += '<img alt="' + t.alt + '" src="' + t.src + '" />', EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="animals">', EmotesBox += "<span>حيوانات وطبيعة</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.animals, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="food">', EmotesBox += "<span>أطعمة ومشروبات</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.food, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="activities">', EmotesBox += "<span>أنشطة</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.activities, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="travel">', EmotesBox += "<span>سفر وأماكن</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.travel, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="things">', EmotesBox += "<span>أشياء</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.things, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="symbols">', EmotesBox += "<span>رموز</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.symbols, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="flags">', EmotesBox += "<span>أعلام</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.flags, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += "</div>", EmotesBox += '<div class="emoticons-bar--box">', EmotesBox += '<span data-emojis="smiles" class="selected"><i class="fal fa-smile"></i><i class="fa fa-smile in"></i></span>', EmotesBox += '<span data-emojis="animals"><i class="fal fa-paw"></i><i class="fa fa-paw in"></i></span>', EmotesBox += '<span data-emojis="food"><i class="fal fa-pumpkin"></i><i class="fa fa-pumpkin in"></i></span>', EmotesBox += '<span data-emojis="activities"><i class="fal fa-volleyball-ball"></i><i class="fa fa-volleyball-ball in"></i></span>', EmotesBox += '<span data-emojis="travel"><i class="fal fa-umbrella"></i><i class="fa fa-umbrella in"></i></span>', EmotesBox += '<span data-emojis="things"><i class="fal fa-lightbulb"></i><i class="fa fa-lightbulb in"></i></span>', EmotesBox += '<span data-emojis="symbols"><i class="fal fa-at"></i><i class="fa fa-at in"></i></span>', EmotesBox += '<span data-emojis="flags"><i class="fal fa-pennant"></i><i class="fa fa-pennant in"></i></span>', EmotesBox += "</div>", EmotesBox += "</div>", 0 == $(this).find(".emoticons--box").length && ($(".emoticons--box").remove(), "html" == t ? $(this).append(EmotesBox) : "chat" == t ? $(this).parent().append(EmotesBox) : $("addpost--ux").append(EmotesBox));
}), $("body").on("click", ".comments--post-statistics---postitem", function () {
  return $(this).parent().parent().find(".videocomments--toggler").show(), 1 != $(this).data("open") ? ($(this).parent().parent().find(".more--post-comments---postitem").click(), $(this).data("open", true)) : ($(this).parent().parent().find(".post-comments--postitem").toggle(), $(this).parent().parent().find(".AddComment").toggle()), false;
}), $("body").on("click", ".more--post-comments---postitem", function () {
  var e = $(this);
  return e.hasClass("waiting") || (e.addClass("waiting"), e.append('<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>'), null != e.data("comment") ? AjaxURL = HomeURL + "/AjaxCenter/CommentsList/" + $(this).data("offset") + "/" + $(this).data("post") + "/" + e.data("comment") + "/" : AjaxURL = HomeURL + "/AjaxCenter/CommentsList/" + $(this).data("offset") + "/" + $(this).data("post") + "/", $.ajax({url: AjaxURL, dataType: "json", type: "POST", success: function (t) {
    e.find(".showbox").remove(), e.parent().parent().find(".comments--post-statistics---postitem").data("open", true), null != e.data("comment") ? (e.parent().find(".reply--comment").append(t.output), e.removeClass("waiting"), e.data("offset", Number(e.data("offset") + t.number)), t.rest < 1 ? e.remove() : e.text("عرض المزيد من الردود (" + t.rest + ")")) : (e.parent().find('ul.inner--post-comments---postitem[data-post="' + e.data("post") + '"]:not([data-comment])').prepend(t.output), e.removeClass("waiting"), e.data("offset", Number(e.data("offset") + t.number)), t.rest < 1 ? e.remove() : e.text("عرض " + t.rest + " تعليقات اضافية"));
  }})), false;
}), $("body").on("keydown keypress keyup", ".TextareaProfile > textarea", function (e) {
  newLines = $(this).val().split("\n").length, $(this).attr("rows", newLines);
}), $("body").on("keypress keyup", ".addcomment-input--post", function (e) {
  if (0 == Currentuser_Logged) data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login"), e.preventDefault(); else {
    $(this);
    if (!$.trim($(this).html()) ? $(this).parent().find("span.placeholder").fadeIn(0) : $(this).parent().find("span.placeholder").fadeOut(0), keyCode = e.keyCode || e.which, 13 === keyCode && !event.shiftKey) return e.preventDefault(), AddNewComment(this), false;
  }
}), $("body").on("focus", ".addcomment-input--post", function (e) {
  $(this).find("*").not("emoji").length > 0 && ($(this).html(""), $(this).parent().find("span.placeholder").fadeIn(0)), 0 == Currentuser_Logged && (data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login"));
}), $("body").on("paste", ".addcomment-input--post", function (e) {
  e.preventDefault();
  var t = (e.originalEvent || e).clipboardData.getData("text/plain");
  document.execCommand("insertHTML", false, stripHTML(t)), $(this).find("*").not("emoji").length > 0 && ($(this).html(""), $(this).parent().find("span.placeholder").fadeIn(0));
}), $(document).on("click", ".AddCommentInput .emoticons--box ul.emoticons-list--box > li", function () {
  src = $(this).find("img").attr("src"), alt = $(this).find("img").attr("alt"), EmojiIcon = '<emoji contenteditable="false" class="emoji--global---wecima s16" tabindex="-1" data-text="true" style="background-image:url(' + src + ');">' + alt + "</emoji>&nbsp;", $(this).parent().parent().parent().parent().parent().parent().parent().find("span.placeholder").fadeOut(0), $(this).parent().parent().parent().parent().parent().parent().parent().find('[contenteditable="true"]').focus(), pasteHtmlAtCaret(EmojiIcon);
}), $("body").on("click", "[data-action]", function () {
  var e = $(this);
  if (HideParentPopover(), "react" == e.data("action")) {
    var t = false;
    if (1 != ISMobile || e.hasClass(".emoji") || (t = true), 1 == t && 1 == e.data("double") || 0 == t) {
      var a = e.data("post"), o = e.data("type"), i = e.data("react");
      0 == Currentuser_Logged ? (data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login")) : (URLAjax = "", $(this).hasClass("emoji") ? (ButtonInsertion = $(this).parent().parent().find(".InnerButton"), ButtonInsertion.attr("class", "InnerButton emoted " + i), "like" == i ? (ButtonInsertion.find("i").attr("class", "fa fa-thumbs-up"), ButtonInsertion.find("span").text("أعجبني")) : (ButtonInsertion.find("i").attr("class", "emoji--icon " + i), ButtonInsertion.find("span").text($(this).data("tooltip"))), ButtonInsertion.data("react", i), e.parent().css({transition: "0s all"}).addClass("close"), URLAjax = HomeURL + "/AjaxCenter/React/" + i + "/" + o + "/" + a + "/" + Currentuser_ID + "/") : (ButtonInsertion = $(this), ButtonInsertion.hasClass("emoted") ? (ButtonInsertion.attr("class", "InnerButton"), ButtonInsertion.find("i").attr("class", "fal fa-thumbs-up"), ButtonInsertion.find("span").text("أعجبني"), ButtonInsertion.data("react", "like")) : (ButtonInsertion.attr("class", "InnerButton emoted"), ButtonInsertion.find("i").attr("class", "fa fa-thumbs-up"), ButtonInsertion.find("span").text("أعجبني")), e.parent().find(".react-area--social").css({transition: "0s all"}).addClass("close"), e.data("double", false), URLAjax = HomeURL + "/AjaxCenter/React/" + i + "/" + o + "/" + a + "/" + Currentuser_ID + "/toggled/"), $.ajax({url: URLAjax, dataType: "json", type: "POST", data: {userID: Currentuser_ID}, success: function (e) {
        $('.post-reactions--post-statistics---postitem[data-post="' + a + '"]').html(e.output), e.notify_mentioned.length > 0 && $.each(e.notify_mentioned, function (e, t) {
          JSONData = {channel: "User@" + t.receiver, executed: {id: t.id, output: t.output, count: t.count}, type: "notification"}, PushTiming("notify", JSONData);
        }), !$.trim(e.reactbox_activity) || (JSONData = {channel: "ActivityBox", executed: {box: e.reactbox_activity}}, PushTiming("notify", JSONData)), null != e.notify && (JSONData = {channel: "User@" + e.notify.receiver, executed: {id: o + "_" + a, output: e.notify.output, count: e.notify.count}, type: "notification"}, PushTiming("notify", JSONData));
      }}));
    } else e.data("double", true);
  } else if ("context" == e.data("action")) "Addpost" == e.data("behavior") ? (data = {title: "<strong>إنشاء منشور</strong>", args: {cat: $("addpost").data("cat")}, ajax: true, folder: "UserActions", content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, e.data("behavior")), PhotoEnabled = false) : (data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, e.data("behavior"))); else if ("context-useractions" == e.data("action")) if ("editcover" == e.data("behavior")) $("innerpaddingauthorcover .cover--contain").addClass("positioning"), $("innerpaddingauthorcover .cover--contain img").removeAttr("style"), $("innerpaddingauthorcover .cover--contain").animate({scrollTop: 0}, 100), $(".profilesettings--cover").hide(), Confirmation("cover-upload", {id: e.data("id")}); else if ("deletecover" == e.data("behavior")) {
    var s;
    s = '<div class="DeletionAlert">', s += "<p>", s += "هل تريد بالتأكيد إزالة صورة الغلاف الخاصة بك؟", s += "</p>", s += '<ul class="DeletionAlert--buttons">', s += '<li class="close--confirmation activable hoverable" data-self="true" data-confirmation="false">إلغاء</li>', s += '<li class="apply--confirmation activable hoverable" data-action="deletecover" data-id="' + e.data("id") + '" data-confirmation="true">تأكيد</li>', s += "</ul>", s += "</div>", data = {title: "<strong>إزالة صورة الغلاف</strong>", ajax: false, content: s}, Context("overlay", data, false);
  } else data = {title: "<strong>" + e.data("title") + "</strong>", ajax: true, folder: "UserActions", content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, e.data("behavior")); else if ("upload-input" == e.data("action")) $('[data-action="upload-input"]').removeClass("focused"), e.addClass("focused"), $("#" + e.data("field")).val(""), "upload-chat-photo" == e.data("field") && $("#" + e.data("field")).data("chatID", e.parent().parent().parent().data("chat")), 0 == $("#" + e.data("field")).length && $("body").append('<input type="file" id="' + e.data("field") + '" style="display:none;" />'), $("#" + e.data("field")).trigger("click"), setTimeout(function () {
    $(".Context--overlays.confirmationbox").remove();
  }, 200); else if ("deny" == e.data("action")) "cover" == e.data("submission") && ($("innerpaddingauthorcover .cover--contain").removeClass("positioning"), $(".LoaderBoxed--Context---overlays").remove(), $(".profilesettings--cover").show(), $("blurred img").attr("src", $("blurred").data("original")), $("innerpaddingauthorcover img").attr("id", $("innerpaddingauthorcover").data("id")), $("innerpaddingauthorcover img").attr("src", $("innerpaddingauthorcover").data("cover")), $("innerpaddingauthorcover img").attr("style", $("innerpaddingauthorcover").data("position"))), $('input[type="file"]').val(""), e.parent().parent().remove(); else if ("coverchoosing--set" == e.data("action")) {
    UniqID();
    $(".Boxed--Context---overlays").append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UserActions/GetPhotoDetails/", dataType: "json", type: "POST", data: {photo: e.data("photo"), user: Currentuser_ID}, success: function (e) {
      "not-allowed" != e.output && ($("parentinnercover > blurred").html('<img src="' + e.blur + '" />'), $("innerpaddingauthorcover .cover--contain").addClass("positioning"), $("innerpaddingauthorcover .cover--contain img").length > 0 ? ($("innerpaddingauthorcover .cover--contain img").removeAttr("style"), $("innerpaddingauthorcover .cover--contain img").attr({src: e.image, id: e.id})) : $("innerpaddingauthorcover .cover--contain").append('<img class="cover--src" src="' + e.image + '" id="' + e.id + '" />'), CloseOverlay(true), $(".LoaderBoxed--Context---overlays").remove(), $(".profilesettings--cover").hide(), Confirmation("cover-upload", e));
    }});
  } else if ("profilepicture--set" == e.data("action")) {
    UniqID();
    $(".Boxed--Context---overlays").append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UserActions/PreviewAvatar/", dataType: "json", type: "POST", data: {photo: e.data("photo"), user: Currentuser_ID}, success: function (t) {
      "not-allowed" != t.output && (ContextBoxed = '<div class="Parent-Boxed--Context---overlays">', ContextBoxed += '<div class="Boxed--Context---overlays">', ContextBoxed += '<div class="title--Context---overlays">', ContextBoxed += "<strong>معاينة صورة الملف الشخصي</strong>", ContextBoxed += '<span class="Close--title---Context----overlays activable" data-self="true"><i class="fas fa-times"></i></span>', ContextBoxed += "</div>", ContextBoxed += '<div class="inner--Context---overlays">', ContextBoxed += '<div class="picturecropping--inner--Context---overlays">', ContextBoxed += '<div class="TextareaProfile"><textarea id="about--profile-picture--texteditor" rows="1"></textarea><strong>الوصف</strong></div>', ContextBoxed += '<div class="cropping--inner---Context----overlays">', ContextBoxed += '<div class="AvatarResizing"></div>', ContextBoxed += "</div>", ContextBoxed += '<div class="privacy--inner--Context---overlays">', ContextBoxed += '<p><i class="fas fa-globe-europe"></i> تظهر صورة ملفك الشخصي للعامة.</p>', ContextBoxed += "</div>", ContextBoxed += "<divider></divider>", ContextBoxed += '<ul class="DeletionAlert--buttons">', ContextBoxed += '<li class="close--confirmation activable hoverable" data-self="true" data-confirmation="false">إلغاء</li>', ContextBoxed += '<li class="apply--confirmation activable hoverable" data-action="saveprofilepicture" data-id="' + e.data("photo") + '" data-confirmation="true">تأكيد</li>', ContextBoxed += "</ul>", ContextBoxed += "</div>", ContextBoxed += "</div>", ContextBoxed += "</div>", ContextBoxed += "</div>", $(".Parent-Boxed--Context---overlays").after(ContextBoxed), $(".AvatarResizing").croppie({url: t.output, mouseWheelZoom: "ctrl", viewport: {width: 300, height: 300, type: "square"}, enableOrientation: true, orientation: 4, setZoom: 1, exif: true, circle: true, type: "base64", format: "jpeg"}), $(".LoaderBoxed--Context---overlays").remove());
    }});
  } else if ("confirm" == e.data("action")) {
    if ("cover" == e.data("submission")) {
      $("innerpaddingauthorcover").append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>');
      var n = $(".cover--contain").scrollTop() / ($(".cover--contain img").height() - $(".cover--contain").height()), r = Math.round(100 * n);
      $.ajax({url: HomeURL + "/AjaxCenter/UserSubmissions/Updatecover/", dataType: "json", type: "POST", data: {cover: e.data("cover"), top: r, user: Currentuser_ID}, success: function (e) {
        $(".WecimaPosts").prepend(e.output), $("innerpaddingauthorcover > a").attr("href", e.url), $("innerpaddingauthorcover .cover--contain").removeClass("positioning"), $(".LoaderBoxed--Context---overlays").remove(), $(".profilesettings--cover").show();
      }});
    }
    $('input[type="file"]').val(""), e.parent().parent().remove();
  }
  return false;
}), $("body").on("click", ".apply--confirmation", function () {
  var e = $(this);
  if ("deletecover" == e.data("action")) e.parent().parent().parent().parent().append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UserSubmissions/Deletecover/", dataType: "json", type: "POST", data: {id: e.data("id"), user: Currentuser_ID}, success: function (e) {
    CloseOverlay(true), $(".cover--src").remove(), $('innerpaddingauthorcover .profilesettings--cover [data-behavior="editcover"]').remove(), $('innerpaddingauthorcover .profilesettings--cover [data-behavior="deletecover"]').remove(), $("innerpaddingauthorcover .profilesettings--cover divider").remove(), $("blurred").html(""), $('[cpd="' + e.output + '"]').remove();
  }}); else if ("acceptremovecontext" == e.data("action")) CloseOverlay(true); else if ("savebio" == e.data("action")) {
    var t;
    (t = $("#textarea--bio--editor").val()).length > 101 ? e.addClass("disabled") : e.hasClass("disabled") || (e.parent().parent().parent().append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UserSubmissions/UpdateBio/", dataType: "json", type: "POST", async: true, data: {bio: t, user: Currentuser_ID, publish: e.data("publish")}, success: function (t) {
      null != t.error ? $("#length--bio--editor").html(t.error) : 1 == e.data("publish") ? ($(".bio--editor").show(), !$.trim(bioCTRL_Z) ? $(".bio--editor").text("إضافة سيرة ذاتية") : $(".bio--editor").text("تعديل"), $("bio").html(bioCTRL_Z), $(".WecimaPosts").prepend(t.block)) : (bioCTRL_Z = t.output, !$.trim(t.output) ? $(".bio--editor").text("إضافة سيرة ذاتية") : $(".bio--editor").text("تعديل"), $("#length--bio--editor").html('تم الحفظ <i class="fas fa-check"></i>'), $(".LoaderBoxed--Context---overlays").remove(), $("bio .apply--confirmation").text("مشاركة الآن"), $("bio .apply--confirmation").data("publish", true), $("bio .close--confirmation").text("تخطي"));
    }}));
  } else if ("saveprofilepicture" == e.data("action")) {
    var a, o;
    e.parent().parent().parent().parent().append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), sizes = [], a = $(".AvatarResizing"), data500 = a.croppie("result", {type: "canvas", size: {width: 500, height: 500}}).then(function (e) {
      sizes[500] = e;
    }), a.croppie("result", {type: "canvas", size: {width: 200, height: 200}}).then(function (e) {
      sizes[200] = e;
    }), a.croppie("result", {type: "canvas", size: {width: 50, height: 50}}).then(function (e) {
      sizes[50] = e;
    }), a.croppie("result", {type: "canvas", size: {width: 40, height: 40}}).then(function (e) {
      sizes[40] = e;
    }), a.croppie("result", {type: "canvas", size: {width: 24, height: 24}}).then(function (e) {
      sizes[24] = e;
    }), o = setInterval(function () {
      null != sizes[200] && null != sizes[500] && null != sizes[50] && null != sizes[40] && null != sizes[24] && (clearInterval(o), sizes = {500: sizes[500], 200: sizes[200], 50: sizes[50], 40: sizes[40], 24: sizes[24]}, $.ajax({url: HomeURL + "/AjaxCenter/UserSubmissions/UpdateProfilePicture/", dataType: "json", type: "POST", async: true, data: {sizes: sizes, content: $("#about--profile-picture--texteditor").val(), photo: e.data("id"), user: Currentuser_ID}, success: function (e) {
        CloseOverlay(true), $(".WecimaPosts").prepend(e.timeline), $.each(e.picture, function (e, t) {
          $("[realppic-" + e + "]").html(t);
        });
      }}));
    }, 300);
  }
}), $("body").on("click", ".close--confirmation", function () {
  "closebio" == $(this).data("action") ? ($("bio").html(bioCTRL_Z), $(".bio--editor").show()) : 1 == $(this).data("self") ? $(this).parent().parent().parent().parent().parent().parent().parent().remove() : "third" == $(this).data("self") ? $(this).parent().parent().parent().parent().parent().parent().parent().remove() : CloseOverlay();
}), $("body").on("mousedown", ".cover--contain.positioning", function (e) {
  return $(this).data("top", true).data("y", e.clientY).data("scrollTop", this.scrollTop), false;
}).on("mouseup", ".cover--contain.positioning", function (e) {
  $(this).data("top", false);
}).on("mousemove", ".cover--contain.positioning", function (e) {
  1 == $(this).data("top") && (this.scrollTop = $(this).data("scrollTop") + $(this).data("y") - e.clientY);
}), $(window).mouseout(function (e) {
  if ($(".cover--contain.positioning").data("top")) try {
    "BODY" != e.originalTarget.nodeName && "HTML" != e.originalTarget.nodeName || $(".cover--contain.positioning").data("top", false);
  } catch (e) {}
}), $("body").on("click", ".remove--comm--previewphoto", function () {
  $(this).parent().parent().find(".addcomment-input--post").data("img", void 0), $(this).parent().remove();
}), $("body").on("change", 'input[type="file"]', function () {
  var e = $(this);
  if (this.files && this.files[0]) {
    var t = new FileReader;
    t.onload = function (t) {
      FileChangeListener(e, t.target.result);
    }, t.readAsDataURL(this.files[0]);
  }
}), $('input[type="file"]').attr("allow", ".jpg, .png, .heif, .webp"), $("body").on("submit", "[form]", function () {
  var e, t, a, o, i = $(this);
  return $(this).find("[data-required]").each(function (e, a) {
    $(a).parent().find("necessary").remove(), !$.trim($(a).val()) && ($(a).after('<necessary data-tooltip="هذا الحقل مطلوب"></necessary>'), t = false);
  }), 0 != t && (e = $(this).serialize(), a = $(this).attr("method"), o = $(this).attr("action"), i.addClass("Checking"), i.append('<div class="loader--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div>'), $.ajax({url: o, dataType: "json", data: e, type: a, success: function (e) {
    i.find(".alert").remove(), "success" == e.alert ? ($(".loader--Context---overlays").html('<i class="fas fa-check-circle"></i>'), location.reload()) : (i.prepend(e.alert), $(".loader--Context---overlays").remove(), i.removeClass("Checking"));
  }})), false;
}), $("body").on("click", "[data-popover]", function () {
  var e, t, a, o, i;
  if (e = $(this), t = UniqID(), a = e.offset().top + e.height() - $(window).scrollTop(), leftorig = e.offset().left, calcul = e.width() / 2, left = leftorig + calcul - 180, left < 16 && (left = 16), i = '<div class="parent--popover" data-hash="' + t + '" style="top:' + a + "px;left:" + left + 'px;">', i += '<div class="inner--parent---popover">', "user--notifications" == e.data("popover") || "user--messenger" == e.data("popover")) {
    for (i += '<div class="inner--parent--notifications">', o = 0; o < 20; o++) i += '<div class="notification--item notification--loading"><a href="#" class="hoverable"><div class="avatar--notification--item"><span class=" wecima--avatar"></span></div><div class="info--notification--item"><strong></strong><time></time></div></a></div>';
    i += "</div>";
  } else i += '<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>';
  (i += "</div>", i += "</div>", e.hasClass("open") ? $('body .parent--popover[data-hash="' + e.data("hash") + '"]').length > 0 ? HideParentPopover(void 0, '.parent--popover[data-hash="' + e.data("hash") + '"]') : HideParentPopover(void 0, '.parent--popover[data-hash="' + t + '"]') : (HideParentPopover(this), e.toggleClass("open")), null == e.data("live")) ? $('body .parent--popover[data-hash="' + e.data("hash") + '"]').length > 0 ? ($(".parent--popover").not($('body .parent--popover[data-hash="' + e.data("hash") + '"]')).hide(), $('body .parent--popover[data-hash="' + e.data("hash") + '"]').toggle()) : (e.data("hash", t), $("body").append(i), $.ajax({url: HomeURL + "/AjaxCenter/Popovers/" + e.data("popover") + "/", dataType: "json", type: "POST", data: e.data("user"), success: function (a) {
    $('.parent--popover[data-hash="' + t + '"] .inner--parent---popover').html(a.output), "user--notifications" == e.data("popover") ? NotificationsRunning() : "user--messenger" == e.data("popover") && MessengerRunning();
  }, error: function () {
    $('.parent--popover[data-hash="' + t + '"]').remove();
  }})) : ("cover" == e.data("popover") ? (i = '<div class="inner--parent---popover">', i += '<div class="softbutton--popover hoverable" data-action="context-useractions" data-title="تحديد صورة" data-behavior="selectcover"><i class="fal fa-images"></i> <span>تحديد صورة</span></div>', i += '<div class="softbutton--popover hoverable" data-action="upload-input" data-field="cover-upload"><i class="fal fa-upload"></i> <span>تحميل صورة</span></div>', $(".cover--src").length > 0 && null != $(".cover--src").attr("src") && !!$.trim($(".cover--src").attr("src")) && (i += '<div class="softbutton--popover hoverable" data-id="' + $(".cover--src").attr("id") + '" data-action="context-useractions" data-title="إعادة تغيير الموضع" data-behavior="editcover"><i class="fal fa-arrows"></i> <span>إعادة تغيير الموضع</span></div>', i += "<divider></divider>", i += '<div class="softbutton--popover hoverable" data-id="' + $(".cover--src").attr("id") + '" data-action="context-useractions" data-title="إزالة" data-behavior="deletecover"><i class="fal fa-trash-alt"></i> <span>إزالة</span></div>'), i += "</div>") : "profile-picture" == e.data("popover") ? (i = '<div class="inner--parent---popover">', null != e.data("profilepicture_url") && (i += '<a href="' + e.data("profilepicture_url") + '" class="softbutton--popover hoverable"><i class="fal fa-book-user"></i> <span>عرض صورة الملف الشخصي</span></a>'), i += '<div class="softbutton--popover hoverable" data-action="context-useractions" data-title="تحديث صورة الملف الشخصي" data-behavior="SelectPhotos"><i class="fal fa-images"></i> <span>تحديث صورة الملف الشخصي</span></div>', i += "</div>") : "confirm--friendrequests" == e.data("popover") && (i = '<div class="inner--parent---popover withouticons">', i += '<div class="softbutton--popover hoverable" data-confirmrequest="true" data-user="' + e.data("user") + '">تأكيد</div>', i += '<div class="softbutton--popover hoverable" data-confirmrequest="false" data-user="' + e.data("user") + '">حذف الطلب</div>', i += "</div>"), e.parent().find(".parent--popover").length > 0 ? ($(".parent--popover").not($(this).parent().find(".parent--popover")).hide(), e.parent().find(".parent--popover").toggle().html(i)) : ($(".parent--popover").hide(), e.parent().append('<div class="parent--popover minipopover" data-hash="' + t + '">' + i + "</div>")));
  return false;
}), $("body").on("click", ".groupsettings--fulldescription", function () {
  var e = $(this);
  return e.hasClass("loaded") ? $(".GroupDescription").html(GroupDescription) : null != FullGroupDescription ? $(".GroupDescription").html(FullGroupDescription) : e.hasClass("loading") || (GroupDescription = $(".GroupDescription").html(), e.addClass("loading"), e.append('<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>'), AjaxSystem = $.ajax({url: HomeURL + "/AjaxCenter/MoreGroupDescription/" + $(this).data("group") + "/", dataType: "json", success: function (t) {
    e.addClass("loaded"), $(".GroupDescription").html(t.output), FullGroupDescription = t.output;
  }})), false;
}), $("body").on("click", ".tabs--watcharea > ul > li", function () {
  var e = $(this).parent().parent().parent().find(".Iframe--Embed--Watcharea");
  $(".tabs--watcharea > ul > li").removeClass("selected"), $(this).addClass("selected"), e.show(), e.find("iframe").hide().attr("src", $(this).data("embed")).on("load", function (e) {
    $(this).show();
  });
}), $("body").on("click", ".PlayEmbed--Embed--Watcharea", function () {
  var e = $(this).parent().find(".Iframe--Embed--Watcharea");
  e.show(), e.find("iframe").hide().attr("src", e.data("fembed")).on("load", function (e) {
    $(this).show();
  });
}), $("body").on("click", "[data-singledownload]", function () {
  var e = $(this), t = $(this).parent().parent();
  e.addClass("loading"), e.append('<svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg>'), setTimeout(function () {
    $('downloadarea[data-trig="' + t.data("trig") + '"]').show(), $("body, html").animate({scrollTop: $('downloadarea[data-trig="' + t.data("trig") + '"]').offset().top - 200}), e.remove();
  }, 1e3);
}), $("body").on("click", ".MoreTeamworkList", function () {
  var e = $(this), t = $(this).parent().find(".Inner--List--Teamwork"), a = t.find("li").length, o = $(this).data("post"), i = "post";
  return null == o && (o = $(this).data("term"), i = "term"), e.addClass("waiting"), $.ajax({url: HomeURL + "/AjaxCenter/MoreActors/" + o + "/" + a + "/" + i + "/", dataType: "json", success: function (a) {
    t.append(a.output), e.removeClass("waiting"), e.find("em").text(e.data("total") - e.parent().find(".Inner--List--Teamwork > li").length), e.parent().find(".Inner--List--Teamwork > li").length == e.data("total") && e.remove();
  }}), false;
});
var Photoloading = false, ScrollingTrigger = function () {
  if ($("iframe").length > 0 && $("iframe[data-ifr]").each(function (e) {
    $(window).scrollTop() + $(window).height() > $(this).offset().top + 100 && ($(this).attr("src", $(this).data("ifr")), $(this).removeAttr("data-ifr"));
  }), $(".inner--photogrid").length > 0 && 0 == Photoloading && $(window).scrollTop() + $(window).height() > $(document).height() - 300) {
    var e = $(".inner--photogrid"), t = e.data("per"), a = 8, o = "";
    for (t < 8 && (a = t), i = 0; i < a; i++) o += "<li class='loading'></li>";
    Photoloading = true, $(".inner--photogrid").append(o), $.ajax({url: HomeURL + "/AjaxCenter/MorePhotos/" + e.data("post") + "/" + t + "/", dataType: "json", success: function (t) {
      $(".inner--photogrid li.loading").remove(), $(".inner--photogrid").append(t.output), e.data("per", t.per), Photoloading = false;
    }});
  }
};
$(window).on("load", ScrollingTrigger), $(window).scroll(ScrollingTrigger);
var MainRightBar = false, MainRightBarAll = false;
function ChangeTitle(e) {
  $(document).prop("title", e);
}
function ChangeURL(e) {
  (e = e.replace("/?ajax=1", "")) != window.location && window.history.pushState({path: e}, "", e);
}
$("body").on("click", ".showmore-userarea--rightbar", function () {
  var e = $(this);
  return 0 != MainRightBar ? (0 == MainRightBarAll && (MainRightBarAll = e.parent().find(".menu-userarea--rightbar").html()), e.hasClass("opened") ? (e.html('<i class="far fa-chevron-down"></i>عرض المزيد').removeClass("opened"), e.parent().find(".menu-userarea--rightbar").html(MainRightBar)) : (e.html('<i class="far fa-chevron-up"></i>عرض أقل').addClass("opened"), e.parent().find(".menu-userarea--rightbar").html(MainRightBarAll))) : (e.css("pointer-events", "none"), e.find(".fa-chevron-down").html('<svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg>'), e.find(".fa-chevron-down").removeAttr("class"), MainRightBar = e.parent().find(".menu-userarea--rightbar").html(), $.ajax({url: HomeURL + "/AjaxCenter/MoreMenus/", dataType: "json", success: function (t) {
    e.parent().find(".menu-userarea--rightbar").append(t.output), e.html('<i class="far fa-chevron-up"></i>عرض أقل').addClass("opened").removeAttr("style");
  }})), false;
});
var AbortStatusAjax = false, RefererURL = false, Scrolling = false;
$("body").on("click", "innerpaddingauthorcover .cover--contain.positioning", function () {
  return false;
}), $("body").on("click", "a", function () {
  var e = $(this), t = (e.attr("href"), "");
  if ((t = null != e.attr("class") ? e.attr("class") : "sss").indexOf("send-message--messenger") > -1 && t.indexOf("more--post-comments---postitem") > -1 && t.indexOf("showmore-userarea--rightbar") > -1 && t.indexOf("inner--friendcontact--item") > -1 && t.indexOf("comments--post-statistics---postitem") > -1 && t.indexOf("PostItemMoreButton") > -1) return false;
}), $("body").on("click", ".closethumb--singlecontainerright", function () {
  $('a[data-action="backbutton"]').trigger("click");
}), $(document).on("keyup keydown keypress", function (e) {
  keyCode = e.keyCode || e.which, 27 == keyCode && ($(".closethumb--singlecontainerright").length > 0 && $(".closethumb--singlecontainerright").trigger("click"), $(".Close--SearchingBox").length > 0 && $(".Close--SearchingBox").trigger("click"));
}), $("body").on("click", "wecima--filter > filterbox > title--filterbox", function () {
  $(this).parent().hasClass("active") ? ($(this).parent().removeClass("active"), $(this).parent().find("list--filterbox").hide(150)) : ($(this).parent().addClass("active"), $(this).parent().find("list--filterbox").show(150));
}), $("body").on("click", "selectfilter", function () {
  $(this).parent().toggleClass("open"), $(this).parent().hasClass("open") ? ($(this).find("span").text("عرض أقل"), $(this).find(".fa-plus").attr("class", "fal fa-minus")) : ($(this).find("span").text("عرض اكثر"), $(this).find(".fa-minus").attr("class", "fal fa-plus"));
});
var Page = 12, FulllistAjax = true;
$("body").on("click", "fulllist", function () {
  if (1 == FulllistAjax) {
    var e = $(this);
    Page += 6, FulllistAjax = false, $.ajax({url: HomeURL + "/AjaxCenter/MoreTaxonomyTerms/" + Page + "/" + e.parent().parent().attr("taxonomy") + "/", dataType: "json", success: function (t) {
      FulllistAjax = true, e.parent().find("inner--list--filterbox").append(t.output);
    }});
  }
}), $("body").on("click", ".RightUI > gototop", function () {
  $(".RightUI").animate({scrollTop: 0});
});
var FilterLoadingAjaxXHR, FilterLoadingNow = false;
function DoFilter(e) {
  var t = [];
  $("wecima--filter").addClass("loading"), 1 == FilterLoadingNow && FilterLoadingAjaxXHR.abort(), FilterLoadingNow = true, $("wecima--filter item.selected").each(function (e, a) {
    t.push({thing: $(a).closest("[filteringbox]").attr("taxonomy"), term: $(a).data("term")});
  });
  var a = HomeURL + "/AjaxCenter/Filtering/";
  $.each(t, function (e, t) {
    a += t.thing + "/" + t.term + "/";
  }), e > 0 && (a += "offset/" + e + "/"), FilterLoadingAjaxXHR = $.ajax({url: a, dataType: "json", success: function (t) {
    $(".Moreposts--paginating").remove(), e > 0 ? $(".Grid--WecimaPosts").append(t.output) : $(".Grid--WecimaPosts").html(t.output), null != t.more_button && ($(".Grid--WecimaPosts").after('<a href="#" data-offset="' + t.more_button_page + '" class="Moreposts--paginating hoverable activable">مزيد من المواضيع <i class="fal fa-angle-left"></i></a>'), $(".pagination").hide()), FilterLoadingNow = false;
  }});
}
$("body").on("click", ".Moreposts--paginating", function () {
  return $(this).hide(), DoFilter($(this).data("offset")), false;
}), $("body").on("click", "dropdownlist > title--dropdownlist > span", function () {
  $(this).closest("filterboxselection").removeClass("open");
}), $("body").on("click", "shortcuts--dropdownlist > span", function () {
  $(this).parent().toggleClass("active");
}), $("body").on("click", "filterboxselection title--filterboxselection", function () {
  var e = $(this).parent();
  $("filterboxselection.open").removeClass("open"), e.toggleClass("open");
}), $("body").on("click", "inner-shortcuts--dropdownlist > item", function () {
  $("inner-shortcuts--dropdownlist > item.selected").removeClass("selected"), $("years--dropdownlist item.selected").removeClass("selected");
}), $("body").on("click", "wecima--filter item", function () {
  var e = $(this);
  e.hasClass("clearall--item") ? e.closest("[filteringbox]").find("item").removeClass("selected") : ($(this).parent().parent().find("inner-shortcuts--dropdownlist").length > 0 && $(this).parent().parent().parent().find("inner-shortcuts--dropdownlist item.selected").removeClass("selected"), e.toggleClass("selected"));
  var t = 0, a = false;
  e.parent().find("item").each(function (e, o) {
    $(o).hasClass("selected") && (a = true, t++);
  }), 1 == a ? (e.closest("filterbox").find("title--filterbox").append("<reset></reset>"), e.closest("filterboxselection").find("title--filterboxselection").addClass("alreadyselected"), e.closest("filterbox").find("title--filterbox").addClass("alreadyselected"), e.closest("filterbox").find("title--filterbox").attr("total", "تم تحديد " + t), e.closest("filterboxselection").find("title--filterboxselection").attr("total", "تم تحديد " + t)) : (e.closest("filterbox").find("title--filterbox reset").remove(), e.closest("filterbox").find("title--filterbox").removeAttr("total"), e.closest("filterbox").find("title--filterbox").removeClass("alreadyselected"), e.closest("filterboxselection").find("title--filterboxselection").removeClass("alreadyselected")), DoFilter(0);
}), $("body").on("dragstart drop", function (e) {
  return e.preventDefault(), false;
}), $(document).mouseup(function (e) {
  var t;
  if ((t = $(".Results--Searching--Overlay, .Searching--Overlay > form-search")).is(e.target) || 0 !== t.has(e.target).length || $(".Close--SearchingBox").trigger("click"), (t = $("chat--tools")).is(e.target) || 0 !== t.has(e.target).length || t.hide(), (t = $(".ProductionsListButton")).is(e.target) || 0 !== t.has(e.target).length || t.removeClass("open"), (t = $("filterboxselection")).is(e.target) || 0 !== t.has(e.target).length || t.removeClass("open"), (t = $(".emoticons--box")).is(e.target) || 0 !== t.has(e.target).length || t.remove(), !(t = $(".emote--item--messages--chatitem, .actions--item--messages--chatitem")).is(e.target) && 0 === t.has(e.target).length) {
    var a = $(".chatitem--chatbody .tools--item--messages--chatitem.focused");
    a.is(e.target) || 0 !== a.has(e.target).length || ($(".chatitem--chatbody .tools--item--messages--chatitem.focused").removeClass("focused"), t.remove());
  }
  (t = $(".parent--popover, [data-popover]")).is(e.target) || 0 !== t.has(e.target).length || HideParentPopover(), (t = $(".Parent-Boxed--Context---overlays")).is(e.target) || 0 !== t.has(e.target).length || CloseOverlay(), moving = false;
}), $(document).mouseover(function (e) {
  var t;
  if ((t = $('[data-button="reactions"], [data-button="mentions"]')).is(e.target) || 0 !== t.has(e.target).length || (t.find("tooltip").remove(), 0 == TooltipAjax && TooltipAbort.abort()), !(t = $("tooltip")).is(e.target) && 0 === t.has(e.target).length) {
    var a = $('[data-button="reactions"]');
    if (!a.is(e.target) && 0 === a.has(e.target).length) {
      var o = $('[data-button="mentions"]');
      o.is(e.target) || 0 !== o.has(e.target).length || t.remove();
    }
  }
}), $("body").on("click", ".emoticons--box > .emoticons-bar--box > span", function (e) {
  $(".emoticons--box > .emoticons-bar--box > span").removeClass("selected"), $(this).addClass("selected"), ThisEL = $(this), ScrollHandler = 0, $('.emoticons-area--box > div[data-key="' + ThisEL.data("emojis") + '"]').prevAll().each(function (e, t) {
    ScrollHandler += $(t).height();
  }), $(".emoticons-area--box").animate({scrollTop: ScrollHandler}, 500);
});
var CommentsArea, PostUploadingPhoto, FullGroupDescription, GroupDescription;
EmoticonsHandler = function () {
  setTimeout(function () {
    $(".emoticons-area--box").scroll(function () {
      ScrollMover = 0, $(".emoticons-area--box > div").each(function (e, t) {
        $(".emoticons-area--box").scrollTop() + $(".emoticons-area--box").height() >= ScrollMover && ($(".emoticons--box > .emoticons-bar--box > span").removeClass("selected"), $('.emoticons--box > .emoticons-bar--box > span[data-emojis="' + $(t).data("key") + '"]').addClass("selected"), 1 != $(t).data("added") && (EmotesBox = "", $.each(Emojis[$(t).data("key")], function (e, t) {
          EmotesBox += "<li>", EmotesBox += '<img alt="' + t.alt + '" src="' + t.src + '" />', EmotesBox += "</li>";
        }), $(t).find(".emoticons-list--box").html(EmotesBox), $(t).data("added", true))), ScrollMover = Number(ScrollMover + $(t).height());
      });
    });
  }, 200);
};
function AddNewComment(e) {
  $(e).find("*").not("emoji").length > 0 && ($(e).html(""), $(e).parent().find("span.placeholder").fadeIn(0));
  var t = $(e).html().replace(/^\s*[\r\n]/gm, "").replace(/\n/g, "<br/>"), a = $(e);
  if ((!!$.trim(t) || null != a.data("img") && 0 != a.data("img")) && 1 == Currentuser_Logged) {
    Hash = UniqID(), CommentItem = '<li class="just-now--comment" data-hash="' + Hash + '">', CommentItem += '<div class="comment-avatar--comments">' + Currentuser_Avatar + "</div>", !$.trim(t) ? CommentItem += '<div class="comment-area--comments emptycontent">' : CommentItem += '<div class="comment-area--comments">', CommentItem += '<div class="inner--comment-area---comments">', CommentItem += '<div class="bg--inner--comment-area---comments">', CommentItem += "<span>" + Currentuser_display_name + "</span>", CommentItem += '<p class="comment-area--content---comments">' + t + "</p>", CommentItem += "</div>", null != a.data("img") && 0 != a.data("img") && (CommentItem += '<div class="photos--comment">', CommentItem += '<div class="parent-item--photos--comment">', CommentItem += '<a href="#" class="item--photos--comment">', CommentItem += '<img src="' + a.data("img") + '" />', CommentItem += '<div class="loader--item--photos--comment">', CommentItem += '<svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg>', CommentItem += "</div>", CommentItem += "</a>", CommentItem += "</div>", CommentItem += "</div>"), CommentItem += "</div>", CommentItem += '<div class="actions--comment-area---comments">', CommentItem += '<a href="#" class="like--actions---post">أعجبني</a>', CommentItem += '<span aria-hidden="true" class="nbsp">&nbsp;·&nbsp;</span>', CommentItem += '<a href="#" class="reply--actions---post">رد</a>', CommentItem += '<span aria-hidden="true" class="nbsp">&nbsp;·&nbsp;</span>', CommentItem += '<time href="#" class="time--actions---post">دقيقة واحدة</time>', CommentItem += "</div>", CommentItem += "</div>", CommentItem += '<input id="Focusing" style="opacity:0;" />', CommentItem += "</li>", null == a.data("type") || "post" == a.data("type") || "series" == a.data("type") ? (CommentsArea = $('.post-comments--postitem[data-post="' + a.data("post") + '"]')).find("ul:not([data-comment])").append(CommentItem) : "reply" == a.data("type") && (CommentsArea = $('.reply--comment[data-comment="' + a.data("comment") + '"]')).append(CommentItem), CommentsArea.closest("singlecontainerleft").length > 0 && ($("#Focusing").focus(), $("#Focusing").remove(), a.focus()), null == a.data("type") || "post" == a.data("type") || "series" == a.data("type") ? AjaxURL = HomeURL + "/AjaxCenter/AddComment/" + a.data("type") + "/" + a.data("post") + "/" : "reply" == a.data("type") && (AjaxURL = HomeURL + "/AjaxCenter/AddComment/comment/" + a.data("post") + "/" + a.data("comment") + "/");
    var o = {comment: t, userID: Currentuser_ID, hash: Hash};
    null != a.data("img") && null != a.data("img") && (o.photo = a.data("img")), $.ajax({url: AjaxURL, dataType: "json", type: "POST", data: o, success: function (e) {
      $('[data-hash="' + Hash + '"]').after(e.comment), $('[data-hash="' + Hash + '"]').remove(), MoreButtonItem = a.parent().parent().parent().parent().find(".more--post-comments---postitem"), MoreButtonItem.data("offset", Number(MoreButtonItem.data("offset") + 1)), null != e.notify1 && (JSONData = {channel: "User@" + e.notify1.receiver, executed: {id: e.notify1.id, output: e.notify1.output, count: e.notify1.count}, type: "notification"}, PushTiming("notify", JSONData)), null != e.notify2 && (JSONData = {channel: "User@" + e.notify2.receiver, executed: {id: e.notify2.id, output: e.notify2.output, count: e.notify2.count}, type: "notification"}, PushTiming("notify", JSONData)), e.notify_mentioned.length > 0 && $.each(e.notify_mentioned, function (e, t) {
        JSONData = {channel: "User@" + t.receiver, executed: {id: t.id, output: t.output, count: t.count}, type: "notification"}, PushTiming("notify", JSONData);
      });
    }}), t = "", a.parent().find("span.placeholder").fadeIn(0), a.html(""), a.parent().parent().parent().find(".comm--previewphoto").remove(), a.data("img", false);
  }
}
function isBase64(e) {
  try {
    return btoa(atob(e)) == e;
  } catch (e) {
    return false;
  }
}
function FileChangeListener(e, t) {
  var a, o, i, s = e.attr("id"), n = new Image;
  n.src = t, n.onerror = function () {
    i = '<div class="DeletionAlert">', i += "<p>", i += "تعذر تحميل صورك. يجب أن يكون حجم الصور أقل من 4 ميجابايت ومحفوظة بتنسيق JPG أو PNG أو TIFF أو HEIF أو WebP.", i += "</p>", i += '<ul class="DeletionAlert--buttons">', i += '<li class="close--confirmation activable hoverable" data-self="third" data-confirmation="false">حسناََ</li>', i += "</ul>", Context("overlay", t = {title: "<strong>خطأ غير متوقع!</strong>", ajax: false, confirmation: true, content: i += "</div>"}, false), $('input[type="file"]').val(""), PostUploadingPhoto = "";
  }, n.onload = function () {
    if (this.width >= 200) if ("cover-upload" == s) $("innerpaddingauthorcover").append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UploadValidate/", dataType: "json", type: "POST", async: true, data: {file: t, folder: "covers", type: "image", user: Currentuser_ID}, success: function (e) {
      $("parentinnercover > blurred").html('<img src="' + e.blur + '" />'), $("innerpaddingauthorcover .cover--contain").addClass("positioning"), $("innerpaddingauthorcover .cover--contain img").length > 0 ? ($("innerpaddingauthorcover .cover--contain img").removeAttr("style"), $("innerpaddingauthorcover .cover--contain img").attr({src: e.image, id: e.id})) : $("innerpaddingauthorcover .cover--contain").append('<img class="cover--src" src="' + e.image + '" id="' + e.id + '" />'), $(".LoaderBoxed--Context---overlays").remove(), $(".profilesettings--cover").hide(), Confirmation(s, e);
    }}); else if ("profile-picture" == s) $(".Boxed--Context---overlays").append('<div class="LoaderBoxed--Context---overlays light"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UploadValidate/", dataType: "json", type: "POST", async: true, data: {file: t, folder: "avatars", type: "image", user: Currentuser_ID}, success: function (e) {
      $(".LoaderBoxed--Context---overlays").remove(), PhotoItem = '<li class="hoverable">', PhotoItem += '<a href="#" data-action="profilepicture--set" data-photo="' + e.id + '">', PhotoItem += '<span style="background-image:url(' + e.url + ');" />', PhotoItem += "</a>", PhotoItem += "</li>", $('.item--grid--photoslibrary[data-photos="avatars"] > ul').prepend(PhotoItem), $('[data-action="profilepicture--set"][data-photo="' + e.id + '"]').trigger("click");
    }}); else if ("upload-post-photo" == s) {
      var n;
      n = '<div class="SelectedPhotoItem">', n += '<img src="' + t + '" />', n += '<span class="Remove-SelectedPhotoItem hoverable activable"><i class="fal fa-times"></i></span>', n += "</div>", $(".scroll--addpost--context").addClass("HasImage"), $(".photo-preview--addpost--context").html(n), setTimeout(function () {
        $(".addpost-input--context").attr("style", "max-height:calc(100vh - 350px - " + $(".SelectedPhotoItem img").height() + "px);");
      }, 200), $(".addpost-input--context").addClass("SmallerText"), $(".addpost-input--context").find("emoji").attr("class", "emoji--global---wecima s20"), PhotoEnabled = true, PostUploadingPhoto = t, CanSavePost();
    } else "prepare-post-photo" == s ? (Context("overlay", t = {title: "<strong>إنشاء منشور</strong>", fastimage: {eleme: "#upload-post-photo", data: t}, args: {cat: $("addpost").data("cat")}, ajax: true, folder: "UserActions", content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, "Addpost"), PhotoEnabled = true) : "upload-chat-photo" == s ? UploadChatPhoto(e, t) : "upload-photo--comment" == s ? (Buttonelem = $('.focused[data-action="upload-input"]'), a = Buttonelem.parent().parent().parent(), a.find(".addcomment-input--post").data("post"), a.find(".addcomment-input--post").data("img", t), o = '<div class="comm--previewphoto">', o += '<img src="' + t + '" />', o += '<span class="remove--comm--previewphoto hoverable activable"><i class="fal fa-times"></i></span>', o += "</div>", a.append(o)) : "upload-photo--reply-comment" == s && (Buttonelem = $('.focused[data-action="upload-input"]'), a = Buttonelem.parent().parent().parent(), a.find(".addcomment-input--post").data("post"), a.find(".addcomment-input--post").data("img", t), o = '<div class="comm--previewphoto">', o += '<img src="' + t + '" />', o += '<span class="remove--comm--previewphoto hoverable activable"><i class="fal fa-times"></i></span>', o += "</div>", a.append(o)); else i = '<div class="DeletionAlert">', i += "<p>", i += "تعذر تحميل صورك. يجب أن يكون حجم الصور أقل من 4 ميجابايت ومحفوظة بتنسيق JPG أو PNG أو TIFF أو HEIF أو WebP.", i += "</p>", i += '<ul class="DeletionAlert--buttons">', i += '<li class="close--confirmation activable hoverable" data-self="third" data-confirmation="false">حسناََ</li>', i += "</ul>", Context("overlay", t = {title: "<strong>خطأ غير متوقع!</strong>", ajax: false, confirmation: true, content: i += "</div>"}, false), $('input[type="file"]').val(""), PostUploadingPhoto = "";
  };
}
$("body").on("click", ".emotions--comment", EmoticonsHandler), $("body").on("click", ".emotions--comment", function (e) {
  var t, a;
  $(this).parent().parent().find(".addcomment-input--post").length > 0 ? (EmotesBox = '<div class="emoticons--box">', t = "html") : $(this).parent().parent().find(".input--editor--chatinput").length > 0 ? (EmotesBox = '<div class="emoticons--box">', t = "chat") : (4, (a = $(".addpost--context").height() + $(".user--addpost---context").height() + 32 + $(".title--Context---overlays").height() - 370) < 370 ? (a = $(".addpost--context").height() + $(".user--addpost---context").height() + 32 + $(".title--Context---overlays").height() + 12, EmotesBox = '<div class="emoticons--box post--triggered-emotes down" style="top:' + a + 'px;left:4px;">') : EmotesBox = '<div class="emoticons--box post--triggered-emotes" style="top:' + a + 'px;left:4px;">', t = "append"), EmotesBox += '<div class="emoticons-area--box">', EmotesBox += '<div data-key="smiles" data-added="true">', EmotesBox += "<span>رموز تعبيرية وأشخاص</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.smiles, function (e, t) {
    EmotesBox += "<li>", EmotesBox += '<img alt="' + t.alt + '" src="' + t.src + '" />', EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="animals">', EmotesBox += "<span>حيوانات وطبيعة</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.animals, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="food">', EmotesBox += "<span>أطعمة ومشروبات</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.food, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="activities">', EmotesBox += "<span>أنشطة</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.activities, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="travel">', EmotesBox += "<span>سفر وأماكن</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.travel, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="things">', EmotesBox += "<span>أشياء</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.things, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="symbols">', EmotesBox += "<span>رموز</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.symbols, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += '<div data-key="flags">', EmotesBox += "<span>أعلام</span>", EmotesBox += '<ul class="emoticons-list--box">', $.each(Emojis.flags, function (e, t) {
    EmotesBox += "<li>", EmotesBox += "<em></em>", EmotesBox += "</li>";
  }), EmotesBox += "</ul>", EmotesBox += "</div>", EmotesBox += "</div>", EmotesBox += '<div class="emoticons-bar--box">', EmotesBox += '<span data-emojis="smiles" class="selected"><i class="fal fa-smile"></i><i class="fa fa-smile in"></i></span>', EmotesBox += '<span data-emojis="animals"><i class="fal fa-paw"></i><i class="fa fa-paw in"></i></span>', EmotesBox += '<span data-emojis="food"><i class="fal fa-pumpkin"></i><i class="fa fa-pumpkin in"></i></span>', EmotesBox += '<span data-emojis="activities"><i class="fal fa-volleyball-ball"></i><i class="fa fa-volleyball-ball in"></i></span>', EmotesBox += '<span data-emojis="travel"><i class="fal fa-umbrella"></i><i class="fa fa-umbrella in"></i></span>', EmotesBox += '<span data-emojis="things"><i class="fal fa-lightbulb"></i><i class="fa fa-lightbulb in"></i></span>', EmotesBox += '<span data-emojis="symbols"><i class="fal fa-at"></i><i class="fa fa-at in"></i></span>', EmotesBox += '<span data-emojis="flags"><i class="fal fa-pennant"></i><i class="fa fa-pennant in"></i></span>', EmotesBox += "</div>", EmotesBox += "</div>", 0 == $(this).find(".emoticons--box").length && ($(".emoticons--box").remove(), "html" == t ? $(this).append(EmotesBox) : "chat" == t ? $(this).parent().append(EmotesBox) : $("addpost--ux").append(EmotesBox));
}), $("body").on("click", ".comments--post-statistics---postitem", function () {
  return $(this).parent().parent().find(".videocomments--toggler").show(), 1 != $(this).data("open") ? ($(this).parent().parent().find(".more--post-comments---postitem").click(), $(this).data("open", true)) : ($(this).parent().parent().find(".post-comments--postitem").toggle(), $(this).parent().parent().find(".AddComment").toggle()), false;
}), $("body").on("click", ".more--post-comments---postitem", function () {
  var e = $(this);
  return e.hasClass("waiting") || (e.addClass("waiting"), e.append('<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>'), null != e.data("comment") ? AjaxURL = HomeURL + "/AjaxCenter/CommentsList/" + $(this).data("offset") + "/" + $(this).data("post") + "/" + e.data("comment") + "/" : AjaxURL = HomeURL + "/AjaxCenter/CommentsList/" + $(this).data("offset") + "/" + $(this).data("post") + "/", $.ajax({url: AjaxURL, dataType: "json", type: "POST", success: function (t) {
    e.find(".showbox").remove(), e.parent().parent().find(".comments--post-statistics---postitem").data("open", true), null != e.data("comment") ? (e.parent().find(".reply--comment").append(t.output), e.removeClass("waiting"), e.data("offset", Number(e.data("offset") + t.number)), t.rest < 1 ? e.remove() : e.text("عرض المزيد من الردود (" + t.rest + ")")) : (e.parent().find('ul.inner--post-comments---postitem[data-post="' + e.data("post") + '"]:not([data-comment])').prepend(t.output), e.removeClass("waiting"), e.data("offset", Number(e.data("offset") + t.number)), t.rest < 1 ? e.remove() : e.text("عرض " + t.rest + " تعليقات اضافية"));
  }})), false;
}), $("body").on("keydown keypress keyup", ".TextareaProfile > textarea", function (e) {
  newLines = $(this).val().split("\n").length, $(this).attr("rows", newLines);
}), $("body").on("keypress keyup", ".addcomment-input--post", function (e) {
  if (0 == Currentuser_Logged) data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login"), e.preventDefault(); else {
    $(this);
    if (!$.trim($(this).html()) ? $(this).parent().find("span.placeholder").fadeIn(0) : $(this).parent().find("span.placeholder").fadeOut(0), keyCode = e.keyCode || e.which, 13 === keyCode && !event.shiftKey) return e.preventDefault(), AddNewComment(this), false;
  }
}), $("body").on("focus", ".addcomment-input--post", function (e) {
  $(this).find("*").not("emoji").length > 0 && ($(this).html(""), $(this).parent().find("span.placeholder").fadeIn(0)), 0 == Currentuser_Logged && (data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login"));
}), $("body").on("paste", ".addcomment-input--post", function (e) {
  e.preventDefault();
  var t = (e.originalEvent || e).clipboardData.getData("text/plain");
  document.execCommand("insertHTML", false, stripHTML(t)), $(this).find("*").not("emoji").length > 0 && ($(this).html(""), $(this).parent().find("span.placeholder").fadeIn(0));
}), $(document).on("click", ".AddCommentInput .emoticons--box ul.emoticons-list--box > li", function () {
  src = $(this).find("img").attr("src"), alt = $(this).find("img").attr("alt"), EmojiIcon = '<emoji contenteditable="false" class="emoji--global---wecima s16" tabindex="-1" data-text="true" style="background-image:url(' + src + ');">' + alt + "</emoji>&nbsp;", $(this).parent().parent().parent().parent().parent().parent().parent().find("span.placeholder").fadeOut(0), $(this).parent().parent().parent().parent().parent().parent().parent().find('[contenteditable="true"]').focus(), pasteHtmlAtCaret(EmojiIcon);
}), $("body").on("click", "[data-action]", function () {
  var e = $(this);
  if (HideParentPopover(), "react" == e.data("action")) {
    var t = false;
    if (1 != ISMobile || e.hasClass(".emoji") || (t = true), 1 == t && 1 == e.data("double") || 0 == t) {
      var a = e.data("post"), o = e.data("type"), i = e.data("react");
      0 == Currentuser_Logged ? (data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, "Login")) : (URLAjax = "", $(this).hasClass("emoji") ? (ButtonInsertion = $(this).parent().parent().find(".InnerButton"), ButtonInsertion.attr("class", "InnerButton emoted " + i), "like" == i ? (ButtonInsertion.find("i").attr("class", "fa fa-thumbs-up"), ButtonInsertion.find("span").text("أعجبني")) : (ButtonInsertion.find("i").attr("class", "emoji--icon " + i), ButtonInsertion.find("span").text($(this).data("tooltip"))), ButtonInsertion.data("react", i), e.parent().css({transition: "0s all"}).addClass("close"), URLAjax = HomeURL + "/AjaxCenter/React/" + i + "/" + o + "/" + a + "/" + Currentuser_ID + "/") : (ButtonInsertion = $(this), ButtonInsertion.hasClass("emoted") ? (ButtonInsertion.attr("class", "InnerButton"), ButtonInsertion.find("i").attr("class", "fal fa-thumbs-up"), ButtonInsertion.find("span").text("أعجبني"), ButtonInsertion.data("react", "like")) : (ButtonInsertion.attr("class", "InnerButton emoted"), ButtonInsertion.find("i").attr("class", "fa fa-thumbs-up"), ButtonInsertion.find("span").text("أعجبني")), e.parent().find(".react-area--social").css({transition: "0s all"}).addClass("close"), e.data("double", false), URLAjax = HomeURL + "/AjaxCenter/React/" + i + "/" + o + "/" + a + "/" + Currentuser_ID + "/toggled/"), $.ajax({url: URLAjax, dataType: "json", type: "POST", data: {userID: Currentuser_ID}, success: function (e) {
        $('.post-reactions--post-statistics---postitem[data-post="' + a + '"]').html(e.output), e.notify_mentioned.length > 0 && $.each(e.notify_mentioned, function (e, t) {
          JSONData = {channel: "User@" + t.receiver, executed: {id: t.id, output: t.output, count: t.count}, type: "notification"}, PushTiming("notify", JSONData);
        }), !$.trim(e.reactbox_activity) || (JSONData = {channel: "ActivityBox", executed: {box: e.reactbox_activity}}, PushTiming("notify", JSONData)), null != e.notify && (JSONData = {channel: "User@" + e.notify.receiver, executed: {id: o + "_" + a, output: e.notify.output, count: e.notify.count}, type: "notification"}, PushTiming("notify", JSONData));
      }}));
    } else e.data("double", true);
  } else if ("context" == e.data("action")) "Addpost" == e.data("behavior") ? (data = {title: "<strong>إنشاء منشور</strong>", args: {cat: $("addpost").data("cat")}, ajax: true, folder: "UserActions", content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, e.data("behavior")), PhotoEnabled = false) : (data = {title: "<loader></loader>", ajax: true, content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, e.data("behavior"))); else if ("context-useractions" == e.data("action")) if ("editcover" == e.data("behavior")) $("innerpaddingauthorcover .cover--contain").addClass("positioning"), $("innerpaddingauthorcover .cover--contain img").removeAttr("style"), $("innerpaddingauthorcover .cover--contain").animate({scrollTop: 0}, 100), $(".profilesettings--cover").hide(), Confirmation("cover-upload", {id: e.data("id")}); else if ("deletecover" == e.data("behavior")) {
    var s;
    s = '<div class="DeletionAlert">', s += "<p>", s += "هل تريد بالتأكيد إزالة صورة الغلاف الخاصة بك؟", s += "</p>", s += '<ul class="DeletionAlert--buttons">', s += '<li class="close--confirmation activable hoverable" data-self="true" data-confirmation="false">إلغاء</li>', s += '<li class="apply--confirmation activable hoverable" data-action="deletecover" data-id="' + e.data("id") + '" data-confirmation="true">تأكيد</li>', s += "</ul>", s += "</div>", data = {title: "<strong>إزالة صورة الغلاف</strong>", ajax: false, content: s}, Context("overlay", data, false);
  } else data = {title: "<strong>" + e.data("title") + "</strong>", ajax: true, folder: "UserActions", content: '<div class="Loading--Context---overlays"><em></em><em></em></div>'}, Context("overlay", data, e.data("behavior")); else if ("upload-input" == e.data("action")) $('[data-action="upload-input"]').removeClass("focused"), e.addClass("focused"), $("#" + e.data("field")).val(""), "upload-chat-photo" == e.data("field") && $("#" + e.data("field")).data("chatID", e.parent().parent().parent().data("chat")), 0 == $("#" + e.data("field")).length && $("body").append('<input type="file" id="' + e.data("field") + '" style="display:none;" />'), $("#" + e.data("field")).trigger("click"), setTimeout(function () {
    $(".Context--overlays.confirmationbox").remove();
  }, 200); else if ("deny" == e.data("action")) "cover" == e.data("submission") && ($("innerpaddingauthorcover .cover--contain").removeClass("positioning"), $(".LoaderBoxed--Context---overlays").remove(), $(".profilesettings--cover").show(), $("blurred img").attr("src", $("blurred").data("original")), $("innerpaddingauthorcover img").attr("id", $("innerpaddingauthorcover").data("id")), $("innerpaddingauthorcover img").attr("src", $("innerpaddingauthorcover").data("cover")), $("innerpaddingauthorcover img").attr("style", $("innerpaddingauthorcover").data("position"))), $('input[type="file"]').val(""), e.parent().parent().remove(); else if ("coverchoosing--set" == e.data("action")) {
    UniqID();
    $(".Boxed--Context---overlays").append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UserActions/GetPhotoDetails/", dataType: "json", type: "POST", data: {photo: e.data("photo"), user: Currentuser_ID}, success: function (e) {
      "not-allowed" != e.output && ($("parentinnercover > blurred").html('<img src="' + e.blur + '" />'), $("innerpaddingauthorcover .cover--contain").addClass("positioning"), $("innerpaddingauthorcover .cover--contain img").length > 0 ? ($("innerpaddingauthorcover .cover--contain img").removeAttr("style"), $("innerpaddingauthorcover .cover--contain img").attr({src: e.image, id: e.id})) : $("innerpaddingauthorcover .cover--contain").append('<img class="cover--src" src="' + e.image + '" id="' + e.id + '" />'), CloseOverlay(true), $(".LoaderBoxed--Context---overlays").remove(), $(".profilesettings--cover").hide(), Confirmation("cover-upload", e));
    }});
  } else if ("profilepicture--set" == e.data("action")) {
    UniqID();
    $(".Boxed--Context---overlays").append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UserActions/PreviewAvatar/", dataType: "json", type: "POST", data: {photo: e.data("photo"), user: Currentuser_ID}, success: function (t) {
      "not-allowed" != t.output && (ContextBoxed = '<div class="Parent-Boxed--Context---overlays">', ContextBoxed += '<div class="Boxed--Context---overlays">', ContextBoxed += '<div class="title--Context---overlays">', ContextBoxed += "<strong>معاينة صورة الملف الشخصي</strong>", ContextBoxed += '<span class="Close--title---Context----overlays activable" data-self="true"><i class="fas fa-times"></i></span>', ContextBoxed += "</div>", ContextBoxed += '<div class="inner--Context---overlays">', ContextBoxed += '<div class="picturecropping--inner--Context---overlays">', ContextBoxed += '<div class="TextareaProfile"><textarea id="about--profile-picture--texteditor" rows="1"></textarea><strong>الوصف</strong></div>', ContextBoxed += '<div class="cropping--inner---Context----overlays">', ContextBoxed += '<div class="AvatarResizing"></div>', ContextBoxed += "</div>", ContextBoxed += '<div class="privacy--inner--Context---overlays">', ContextBoxed += '<p><i class="fas fa-globe-europe"></i> تظهر صورة ملفك الشخصي للعامة.</p>', ContextBoxed += "</div>", ContextBoxed += "<divider></divider>", ContextBoxed += '<ul class="DeletionAlert--buttons">', ContextBoxed += '<li class="close--confirmation activable hoverable" data-self="true" data-confirmation="false">إلغاء</li>', ContextBoxed += '<li class="apply--confirmation activable hoverable" data-action="saveprofilepicture" data-id="' + e.data("photo") + '" data-confirmation="true">تأكيد</li>', ContextBoxed += "</ul>", ContextBoxed += "</div>", ContextBoxed += "</div>", ContextBoxed += "</div>", ContextBoxed += "</div>", $(".Parent-Boxed--Context---overlays").after(ContextBoxed), $(".AvatarResizing").croppie({url: t.output, mouseWheelZoom: "ctrl", viewport: {width: 300, height: 300, type: "square"}, enableOrientation: true, orientation: 4, setZoom: 1, exif: true, circle: true, type: "base64", format: "jpeg"}), $(".LoaderBoxed--Context---overlays").remove());
    }});
  } else if ("confirm" == e.data("action")) {
    if ("cover" == e.data("submission")) {
      $("innerpaddingauthorcover").append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>');
      var n = $(".cover--contain").scrollTop() / ($(".cover--contain img").height() - $(".cover--contain").height()), r = Math.round(100 * n);
      $.ajax({url: HomeURL + "/AjaxCenter/UserSubmissions/Updatecover/", dataType: "json", type: "POST", data: {cover: e.data("cover"), top: r, user: Currentuser_ID}, success: function (e) {
        $(".WecimaPosts").prepend(e.output), $("innerpaddingauthorcover > a").attr("href", e.url), $("innerpaddingauthorcover .cover--contain").removeClass("positioning"), $(".LoaderBoxed--Context---overlays").remove(), $(".profilesettings--cover").show();
      }});
    }
    $('input[type="file"]').val(""), e.parent().parent().remove();
  }
  return false;
}), $("body").on("click", ".apply--confirmation", function () {
  var e = $(this);
  if ("deletecover" == e.data("action")) e.parent().parent().parent().parent().append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UserSubmissions/Deletecover/", dataType: "json", type: "POST", data: {id: e.data("id"), user: Currentuser_ID}, success: function (e) {
    CloseOverlay(true), $(".cover--src").remove(), $('innerpaddingauthorcover .profilesettings--cover [data-behavior="editcover"]').remove(), $('innerpaddingauthorcover .profilesettings--cover [data-behavior="deletecover"]').remove(), $("innerpaddingauthorcover .profilesettings--cover divider").remove(), $("blurred").html(""), $('[cpd="' + e.output + '"]').remove();
  }}); else if ("acceptremovecontext" == e.data("action")) CloseOverlay(true); else if ("savebio" == e.data("action")) {
    var t;
    (t = $("#textarea--bio--editor").val()).length > 101 ? e.addClass("disabled") : e.hasClass("disabled") || (e.parent().parent().parent().append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), $.ajax({url: HomeURL + "/AjaxCenter/UserSubmissions/UpdateBio/", dataType: "json", type: "POST", async: true, data: {bio: t, user: Currentuser_ID, publish: e.data("publish")}, success: function (t) {
      null != t.error ? $("#length--bio--editor").html(t.error) : 1 == e.data("publish") ? ($(".bio--editor").show(), !$.trim(bioCTRL_Z) ? $(".bio--editor").text("إضافة سيرة ذاتية") : $(".bio--editor").text("تعديل"), $("bio").html(bioCTRL_Z), $(".WecimaPosts").prepend(t.block)) : (bioCTRL_Z = t.output, !$.trim(t.output) ? $(".bio--editor").text("إضافة سيرة ذاتية") : $(".bio--editor").text("تعديل"), $("#length--bio--editor").html('تم الحفظ <i class="fas fa-check"></i>'), $(".LoaderBoxed--Context---overlays").remove(), $("bio .apply--confirmation").text("مشاركة الآن"), $("bio .apply--confirmation").data("publish", true), $("bio .close--confirmation").text("تخطي"));
    }}));
  } else if ("saveprofilepicture" == e.data("action")) {
    var a, o;
    e.parent().parent().parent().parent().append('<div class="LoaderBoxed--Context---overlays"><div class="InnerLoaderBoxed--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div></div>'), sizes = [], a = $(".AvatarResizing"), data500 = a.croppie("result", {type: "canvas", size: {width: 500, height: 500}}).then(function (e) {
      sizes[500] = e;
    }), a.croppie("result", {type: "canvas", size: {width: 200, height: 200}}).then(function (e) {
      sizes[200] = e;
    }), a.croppie("result", {type: "canvas", size: {width: 50, height: 50}}).then(function (e) {
      sizes[50] = e;
    }), a.croppie("result", {type: "canvas", size: {width: 40, height: 40}}).then(function (e) {
      sizes[40] = e;
    }), a.croppie("result", {type: "canvas", size: {width: 24, height: 24}}).then(function (e) {
      sizes[24] = e;
    }), o = setInterval(function () {
      null != sizes[200] && null != sizes[500] && null != sizes[50] && null != sizes[40] && null != sizes[24] && (clearInterval(o), sizes = {500: sizes[500], 200: sizes[200], 50: sizes[50], 40: sizes[40], 24: sizes[24]}, $.ajax({url: HomeURL + "/AjaxCenter/UserSubmissions/UpdateProfilePicture/", dataType: "json", type: "POST", async: true, data: {sizes: sizes, content: $("#about--profile-picture--texteditor").val(), photo: e.data("id"), user: Currentuser_ID}, success: function (e) {
        CloseOverlay(true), $(".WecimaPosts").prepend(e.timeline), $.each(e.picture, function (e, t) {
          $("[realppic-" + e + "]").html(t);
        });
      }}));
    }, 300);
  }
}), $("body").on("click", ".close--confirmation", function () {
  "closebio" == $(this).data("action") ? ($("bio").html(bioCTRL_Z), $(".bio--editor").show()) : 1 == $(this).data("self") ? $(this).parent().parent().parent().parent().parent().parent().parent().remove() : "third" == $(this).data("self") ? $(this).parent().parent().parent().parent().parent().parent().parent().remove() : CloseOverlay();
}), $("body").on("mousedown", ".cover--contain.positioning", function (e) {
  return $(this).data("top", true).data("y", e.clientY).data("scrollTop", this.scrollTop), false;
}).on("mouseup", ".cover--contain.positioning", function (e) {
  $(this).data("top", false);
}).on("mousemove", ".cover--contain.positioning", function (e) {
  1 == $(this).data("top") && (this.scrollTop = $(this).data("scrollTop") + $(this).data("y") - e.clientY);
}), $(window).mouseout(function (e) {
  if ($(".cover--contain.positioning").data("top")) try {
    "BODY" != e.originalTarget.nodeName && "HTML" != e.originalTarget.nodeName || $(".cover--contain.positioning").data("top", false);
  } catch (e) {}
}), $("body").on("click", ".remove--comm--previewphoto", function () {
  $(this).parent().parent().find(".addcomment-input--post").data("img", void 0), $(this).parent().remove();
}), $("body").on("change", 'input[type="file"]', function () {
  var e = $(this);
  if (this.files && this.files[0]) {
    var t = new FileReader;
    t.onload = function (t) {
      FileChangeListener(e, t.target.result);
    }, t.readAsDataURL(this.files[0]);
  }
}), $('input[type="file"]').attr("allow", ".jpg, .png, .heif, .webp"), $("body").on("submit", "[form]", function () {
  var e, t, a, o, i = $(this);
  return $(this).find("[data-required]").each(function (e, a) {
    $(a).parent().find("necessary").remove(), !$.trim($(a).val()) && ($(a).after('<necessary data-tooltip="هذا الحقل مطلوب"></necessary>'), t = false);
  }), 0 != t && (e = $(this).serialize(), a = $(this).attr("method"), o = $(this).attr("action"), i.addClass("Checking"), i.append('<div class="loader--Context---overlays"><div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div></div>'), $.ajax({url: o, dataType: "json", data: e, type: a, success: function (e) {
    i.find(".alert").remove(), "success" == e.alert ? ($(".loader--Context---overlays").html('<i class="fas fa-check-circle"></i>'), location.reload()) : (i.prepend(e.alert), $(".loader--Context---overlays").remove(), i.removeClass("Checking"));
  }})), false;
}), $("body").on("click", "[data-popover]", function () {
  var e, t, a, o, i;
  if (e = $(this), t = UniqID(), a = e.offset().top + e.height() - $(window).scrollTop(), leftorig = e.offset().left, calcul = e.width() / 2, left = leftorig + calcul - 180, left < 16 && (left = 16), i = '<div class="parent--popover" data-hash="' + t + '" style="top:' + a + "px;left:" + left + 'px;">', i += '<div class="inner--parent---popover">', "user--notifications" == e.data("popover") || "user--messenger" == e.data("popover")) {
    for (i += '<div class="inner--parent--notifications">', o = 0; o < 20; o++) i += '<div class="notification--item notification--loading"><a href="#" class="hoverable"><div class="avatar--notification--item"><span class=" wecima--avatar"></span></div><div class="info--notification--item"><strong></strong><time></time></div></a></div>';
    i += "</div>";
  } else i += '<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>';
  (i += "</div>", i += "</div>", e.hasClass("open") ? $('body .parent--popover[data-hash="' + e.data("hash") + '"]').length > 0 ? HideParentPopover(void 0, '.parent--popover[data-hash="' + e.data("hash") + '"]') : HideParentPopover(void 0, '.parent--popover[data-hash="' + t + '"]') : (HideParentPopover(this), e.toggleClass("open")), null == e.data("live")) ? $('body .parent--popover[data-hash="' + e.data("hash") + '"]').length > 0 ? ($(".parent--popover").not($('body .parent--popover[data-hash="' + e.data("hash") + '"]')).hide(), $('body .parent--popover[data-hash="' + e.data("hash") + '"]').toggle()) : (e.data("hash", t), $("body").append(i), $.ajax({url: HomeURL + "/AjaxCenter/Popovers/" + e.data("popover") + "/", dataType: "json", type: "POST", data: e.data("user"), success: function (a) {
    $('.parent--popover[data-hash="' + t + '"] .inner--parent---popover').html(a.output), "user--notifications" == e.data("popover") ? NotificationsRunning() : "user--messenger" == e.data("popover") && MessengerRunning();
  }, error: function () {
    $('.parent--popover[data-hash="' + t + '"]').remove();
  }})) : ("cover" == e.data("popover") ? (i = '<div class="inner--parent---popover">', i += '<div class="softbutton--popover hoverable" data-action="context-useractions" data-title="تحديد صورة" data-behavior="selectcover"><i class="fal fa-images"></i> <span>تحديد صورة</span></div>', i += '<div class="softbutton--popover hoverable" data-action="upload-input" data-field="cover-upload"><i class="fal fa-upload"></i> <span>تحميل صورة</span></div>', $(".cover--src").length > 0 && null != $(".cover--src").attr("src") && !!$.trim($(".cover--src").attr("src")) && (i += '<div class="softbutton--popover hoverable" data-id="' + $(".cover--src").attr("id") + '" data-action="context-useractions" data-title="إعادة تغيير الموضع" data-behavior="editcover"><i class="fal fa-arrows"></i> <span>إعادة تغيير الموضع</span></div>', i += "<divider></divider>", i += '<div class="softbutton--popover hoverable" data-id="' + $(".cover--src").attr("id") + '" data-action="context-useractions" data-title="إزالة" data-behavior="deletecover"><i class="fal fa-trash-alt"></i> <span>إزالة</span></div>'), i += "</div>") : "profile-picture" == e.data("popover") ? (i = '<div class="inner--parent---popover">', null != e.data("profilepicture_url") && (i += '<a href="' + e.data("profilepicture_url") + '" class="softbutton--popover hoverable"><i class="fal fa-book-user"></i> <span>عرض صورة الملف الشخصي</span></a>'), i += '<div class="softbutton--popover hoverable" data-action="context-useractions" data-title="تحديث صورة الملف الشخصي" data-behavior="SelectPhotos"><i class="fal fa-images"></i> <span>تحديث صورة الملف الشخصي</span></div>', i += "</div>") : "confirm--friendrequests" == e.data("popover") && (i = '<div class="inner--parent---popover withouticons">', i += '<div class="softbutton--popover hoverable" data-confirmrequest="true" data-user="' + e.data("user") + '">تأكيد</div>', i += '<div class="softbutton--popover hoverable" data-confirmrequest="false" data-user="' + e.data("user") + '">حذف الطلب</div>', i += "</div>"), e.parent().find(".parent--popover").length > 0 ? ($(".parent--popover").not($(this).parent().find(".parent--popover")).hide(), e.parent().find(".parent--popover").toggle().html(i)) : ($(".parent--popover").hide(), e.parent().append('<div class="parent--popover minipopover" data-hash="' + t + '">' + i + "</div>")));
  return false;
}), $("body").on("click", ".groupsettings--fulldescription", function () {
  var e = $(this);
  return e.hasClass("loaded") ? $(".GroupDescription").html(GroupDescription) : null != FullGroupDescription ? $(".GroupDescription").html(FullGroupDescription) : e.hasClass("loading") || (GroupDescription = $(".GroupDescription").html(), e.addClass("loading"), e.append('<div class="showbox"><div class="loader"><svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg></div></div>'), AjaxSystem = $.ajax({url: HomeURL + "/AjaxCenter/MoreGroupDescription/" + $(this).data("group") + "/", dataType: "json", success: function (t) {
    e.addClass("loaded"), $(".GroupDescription").html(t.output), FullGroupDescription = t.output;
  }})), false;
}), $("body").on("click", ".tabs--watcharea > ul > li", function () {
  var e = $(this).parent().parent().parent().find(".Iframe--Embed--Watcharea");
  $(".tabs--watcharea > ul > li").removeClass("selected"), $(this).addClass("selected"), e.show(), e.find("iframe").hide().attr("src", $(this).data("embed")).on("load", function (e) {
    $(this).show();
  });
}), $("body").on("click", ".PlayEmbed--Embed--Watcharea", function () {
  var e = $(this).parent().find(".Iframe--Embed--Watcharea");
  e.show(), e.find("iframe").hide().attr("src", e.data("fembed")).on("load", function (e) {
    $(this).show();
  });
}), $("body").on("click", "[data-singledownload]", function () {
  var e = $(this), t = $(this).parent().parent();
  e.addClass("loading"), e.append('<svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg>'), setTimeout(function () {
    $('downloadarea[data-trig="' + t.data("trig") + '"]').show(), $("body, html").animate({scrollTop: $('downloadarea[data-trig="' + t.data("trig") + '"]').offset().top - 200}), e.remove();
  }, 1e3);
}), $("body").on("click", ".MoreTeamworkList", function () {
  var e = $(this), t = $(this).parent().find(".Inner--List--Teamwork"), a = t.find("li").length, o = $(this).data("post"), i = "post";
  return null == o && (o = $(this).data("term"), i = "term"), e.addClass("waiting"), $.ajax({url: HomeURL + "/AjaxCenter/MoreActors/" + o + "/" + a + "/" + i + "/", dataType: "json", success: function (a) {
    t.append(a.output), e.removeClass("waiting"), e.find("em").text(e.data("total") - e.parent().find(".Inner--List--Teamwork > li").length), e.parent().find(".Inner--List--Teamwork > li").length == e.data("total") && e.remove();
  }}), false;
});
Photoloading = false, ScrollingTrigger = function () {
  if ($("iframe").length > 0 && $("iframe[data-ifr]").each(function (e) {
    $(window).scrollTop() + $(window).height() > $(this).offset().top + 100 && ($(this).attr("src", $(this).data("ifr")), $(this).removeAttr("data-ifr"));
  }), $(".inner--photogrid").length > 0 && 0 == Photoloading && $(window).scrollTop() + $(window).height() > $(document).height() - 300) {
    var e = $(".inner--photogrid"), t = e.data("per"), a = 8, o = "";
    for (t < 8 && (a = t), i = 0; i < a; i++) o += "<li class='loading'></li>";
    Photoloading = true, $(".inner--photogrid").append(o), $.ajax({url: HomeURL + "/AjaxCenter/MorePhotos/" + e.data("post") + "/" + t + "/", dataType: "json", success: function (t) {
      $(".inner--photogrid li.loading").remove(), $(".inner--photogrid").append(t.output), e.data("per", t.per), Photoloading = false;
    }});
  }
};
$(window).on("load", ScrollingTrigger), $(window).scroll(ScrollingTrigger);
var HideAMoment, AjaxNavigationXHR;
MainRightBar = false, MainRightBarAll = false;
function ChangeTitle(e) {
  $(document).prop("title", e);
}
function ChangeURL(e) {
  (e = e.replace("/?ajax=1", "")) != window.location && window.history.pushState({path: e}, "", e);
}
$("body").on("click", ".showmore-userarea--rightbar", function () {
  var e = $(this);
  return 0 != MainRightBar ? (0 == MainRightBarAll && (MainRightBarAll = e.parent().find(".menu-userarea--rightbar").html()), e.hasClass("opened") ? (e.html('<i class="far fa-chevron-down"></i>عرض المزيد').removeClass("opened"), e.parent().find(".menu-userarea--rightbar").html(MainRightBar)) : (e.html('<i class="far fa-chevron-up"></i>عرض أقل').addClass("opened"), e.parent().find(".menu-userarea--rightbar").html(MainRightBarAll))) : (e.css("pointer-events", "none"), e.find(".fa-chevron-down").html('<svg class="circular" viewBox="25 25 50 50"><circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10"/></svg>'), e.find(".fa-chevron-down").removeAttr("class"), MainRightBar = e.parent().find(".menu-userarea--rightbar").html(), $.ajax({url: HomeURL + "/AjaxCenter/MoreMenus/", dataType: "json", success: function (t) {
    e.parent().find(".menu-userarea--rightbar").append(t.output), e.html('<i class="far fa-chevron-up"></i>عرض أقل').addClass("opened").removeAttr("style");
  }})), false;
});
AbortStatusAjax = false, RefererURL = false, Scrolling = false;
function dataPopupClosed(e) {
  if (e) {
    $("payments-wecima-container").css("opacity", "0"), fastspring.builder.reset();
    var t = HomeURL + "/AjaxCenter/Checkout/";
    $.ajax({type: "POST", url: t, dataType: "json", data: {order: e.id}, success: function (e) {
      $("payments-wecima-container").css("opacity", "1"), e.success ? ($("payments-wecima-container").addClass("succeed"), $("payments-wecima-container").html('<i class="fa fa-check"></i><p>تم الإشتراك بنجاح</p><strong>سارية حتى : ' + e.success + "</strong>"), setTimeout(function () {
        location.href = HomeURL;
      }, 3e3)) : ($("payments-wecima-container > .alert").remove(), $("payments-wecima-container").prepend('<div class="alert alert-error">' + e.errors + "</div>"));
    }, error: function (e, t) {
      console.log(e), console.log(t);
    }});
  }
}
$("body").on("click", "innerpaddingauthorcover .cover--contain.positioning", function () {
  return false;
}), $("body").on("click", "a", function () {
  var e = $(this), t = (e.attr("href"), "");
  if ((t = null != e.attr("class") ? e.attr("class") : "sss").indexOf("send-message--messenger") > -1 && t.indexOf("more--post-comments---postitem") > -1 && t.indexOf("showmore-userarea--rightbar") > -1 && t.indexOf("inner--friendcontact--item") > -1 && t.indexOf("comments--post-statistics---postitem") > -1 && t.indexOf("PostItemMoreButton") > -1) return false;
}), $("body").on("click", ".closethumb--singlecontainerright", function () {
  $('a[data-action="backbutton"]').trigger("click");
}), $(document).on("keyup keydown keypress", function (e) {
  keyCode = e.keyCode || e.which, 27 == keyCode && ($(".closethumb--singlecontainerright").length > 0 && $(".closethumb--singlecontainerright").trigger("click"), $(".Close--SearchingBox").length > 0 && $(".Close--SearchingBox").trigger("click"));
}), $("body").on("click", ".PriceTable > ul > li", function () {
  $(".PriceTable > ul > li").removeClass("selected featured"), $(this).addClass("selected"), $(".PriceTable_Footer > a").addClass("hoverable activable").removeClass("disabled");
}), $("body").on("click", ".PriceTable_Footer > a.ChoosePlan", function () {
  return $(".PriceTable > ul > li.selected").length > 0 && (fastspring.builder.clean(), fastspring.builder.add($(".PriceTable > ul > li.selected").data("id")), fastspring.builder.checkout()), false;
});