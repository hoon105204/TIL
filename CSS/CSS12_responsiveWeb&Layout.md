# CSS12_responsiveWeb & Layout

> layout과 media query를 이용하여 화면 가로 크기에 따라 변하는 웹 구성
> 

### Result

<img src=".\image\responseWeb.gif" alt="responseWeb" style="zoom:50%;" />

### html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ResposibleWeb</title>
    <!--css파일 불러오기-->
    <link href="./resource/header.css" rel="stylesheet" type="text/css">
    <link href="./resource/nav.css" rel="stylesheet" type="text/css">
    <link href="./resource/contents.css" rel="stylesheet" type="text/css">

</head>
<body>
    <header class="header">
        <div class="header_wrapper">
            <div class="header_left">
                <button class="header_menu">&#9776;</button> <!--가로 줄3개 버튼-->
                <span class="header_title">TestMenu</span>
            </div>
            <div class="header_center">
                <form class="header_form" onsubmit="return false;">
                    <input class="header_input_text" type="text" name="search">
                    <button class="header_input_button">검색</button>
                </form>
            </div>
            <div class="header_right">
                <button class="header_search">&#128269;</button>
                <div class="header_img"></div>
            </div>
        </div>
    </header>

    <nav class="nav">
        <ul class="nav_wrapper">
            <li>
                <div class="nav_icon">📽️</div>
                <div class="nav_menu">메뉴</div>
            </li>
            <li>
                <div class="nav_icon nav_icon2">🧲</div>
                <div class="nav_menu">메뉴</div>
            </li>
            <li>
                <div class="nav_icon nav_icon2">🎈</div>
                <div class="nav_menu">메뉴</div>
            </li>
        </ul>
    </nav>

    <section class="contents">
        <div class="content_wrapper">
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
            <div class="content">
                <img class="content_img" src="../1_html/image/img4.jpg">
                <div class="content_info">
                    <div class="content_profile"></div>
                    <div class="content_title">Title</div>
                    <div class="content_writer">이태영</div>
                    <div class="content_count">조회수 10.2만</div>
                </div>
            </div>
        </div>
    </section>
</body>
</html>
```

### header.css

```css
.header{
    position: fixed;
    top: 0;
    left: 0;
    box-shadow: 0 0 3px black;
    width: 100%;
    z-index: 10;
    background-color: white;
}

.header_wrapper{
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.header_left{
    height: 35px;
    line-height: 35px;
}

.header_menu{
    border: none;
    font-size: 1.2rem;
    display: none;
}
.header_title{
    font-size: 1.2rem;
    margin-left: 10px;
}

.header_center{
    width: 50%;
}

.header_form{
    display: flex;
    max-width: 100%;
}
.header_input_text{
    width: calc(100% - 70px);
    height: 25px;
    border-right: none;
    border-bottom: black solid 2px;
}
.header_input_button{
    width: 70px;
    border-left: none;
}

.header_right{
    display: flex;
    margin-right: 10px;
}
.header_search{
    border: none;
    background-color: transparent; /* 투명하게 */
    font-size: 1.5rem;

    display: none;
}
.header_img{
    width: 35px;
    height: 35px;
    border-radius: 50%;
    background-color: cyan;
    /* background-image: url(../../1_html/image/img03.png);
    background-size: 35px 35px; */
}

@media screen and (max-width: 500px){
    .header_search{
        display: block;
    }

    .header_menu{
        display: block;
    }

    .header_title{
        display: none;
    }
    .header_center{
        display: none;
    }
}
```

### nav.css

```css
.nav{
    position: fixed;
    top: 0;
    left: 0;
    z-index: 5;
}

.nav_wrapper{
    min-width: 100px;
    min-height: 100vh;
    list-style: none;
    padding-top: 70px;
}
.nav_wrapper>li>div{
    padding: 5px;
    padding-bottom: 0px;
    width: 60px;
}
.nav_menu{
    font-size: 1.1rem;
}
.nav_icon{
    font-size: 1.6rem;
}
.nav_icon2{
    margin-top: 15px;
}

ul>li>div:hover{
    cursor: pointer;
}

@media screen and (max-width: 800px) {
    .nav_menu{
        display: none;
    }
}

@media screen and (max-width: 500px) {
    .nav_wrapper{
        display: none;
    }
}
```

### content.css

```css
.content_wrapper{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin: 60px 0 0 100px;
    padding: 20px 0 0 20px;
}

.content{
    width: 24%;
    margin-right: 1px;
}
.content_img{
    max-width: 100%;
}

.content_profile{
    width: 36px;
    height: 36px;
    border-radius: 50%;
    background-color: blanchedalmond;
    float: left;
    margin-top: 13px;
    margin-right: 10px;
}

@media screen and (max-width: 1000px){
    .content{
        width: 33%;
    }
}

@media screen and (max-width: 800px){
    .content{
        width: 49%;
    }
}

@media screen and (max-width: 500px){
    .content{
        width: 100%;
    }

    .content_wrapper{
        margin: 60px 0 0 20px;
    }
}
```