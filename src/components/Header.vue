<template>
 <header class="c-header">
    <div class="c-header__top">
        <div class="container">
            <div class="row align-items-center">
                <div class="col-md-4 logo text-left">
                    <img src="../assets/images/logo.png" alt="logo"/>
                </div>
                <div class="col-md-8">
                    <div class="row align-items-center justify-content-between">
                        <div class="col-md-auto">
                            <div class="icon email"></div>
                            <span class="c-header__contact-text">
                                noostar@gmail.com
                            </span>
                        </div>
                        <div class="col-md-auto">
                            <div class="icon phone"></div>
                            <span class="c-header__contact-text">
                                +38 (050) 123-45-67
                            </span>
                        </div>
                       <div class="btn-group col-md-auto">
                        <button type="button" class="btn lang dropdown-toggle" data-toggle="dropdown">
                           English
                        </button>
                        <div class="dropdown-menu">
                          <a class="dropdown-item lang" href="#">English</a>
                          <a class="dropdown-item lang" href="#">Russian</a>
                          <a class="dropdown-item lang" href="#">Ukrainian</a>
                        </div>
                      </div>                            
                       
                        <div class="col-md-auto">
                            <div class="orange_btn">
                                Стать студентом
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</header>
</template>

<script>
    export default{
        
    }
</script>

<style lang="less">


@mainOrange: #ff5215;
@mainBlue: #0a063c;
@text: #5a5a5a;
@border: #e8e8e8;

.logo {

}
.c-header {
    &__top {
        background-color: @mainBlue;
        padding: 20px 0;
    }
    &__contact-text {
        font-family: Lato;
        font-weight: 600;
        font-size: 15px;
        color: white;
        text-align: left;
    }
    &__content {

    }
}

.c-button {
    background-color: @mainOrange;
    max-width: 180px;
    display: block;
    width: 100%;
    padding: 12px 12px 8px;
    border: none;
    box-shadow: none;
    border-radius: 4px;
    color: white;
    cursor: pointer;
    font-weight: bold;
    font-family: Muller;
    text-align: center;
    text-transform: uppercase;
    font-size: 13px;
    line-height: 13px;
    &:hover{
        color: white;
    }
    &--right{
        margin-top: 20px;
        float: right;
        max-width: 140px;
    }
    &--biggest{
        max-width: 190px;
    }
}
.c-invite {
    min-height: 65vh;
    padding: 20px 0;
    width: 100%;
    color: white;
    background: url('../assets/images/bg-header.jpg') center no-repeat;
    background-size: cover;
    font-family: Muller;
    display: flex;
    align-items: center;
    &__title {
        font-weight: bold;
        font-size: 36px;
        line-height: 36px;
        margin-bottom: 25px;
        text-align:left;
    }
    &__text {
        font-size: 18px;
        line-height: 18px;
        margin-bottom: 15px;
        text-align:left;
    }
}
.icon{
    width: 12px;
    height: 12px;
    display: inline-block;
}
.email{
     background: url('../assets/images/email_icon.png') center/cover no-repeat content-box;
}
.phone{
     background: url('../assets/images/phone_icon.png') center/cover no-repeat content-box;
}
.lang{  
    padding: 7px 15px 7px;
    border: 1px grey;
    box-shadow: none;
    border-radius: 4px;
    color:grey;
    font-family: Muller;
    font-size: 13px;   
    background-color: white;
}

@media (max-width: 767px) {
    .row {
        margin: 0 !important;
    }
    .col-md-auto {
        width: auto;
        padding: 5px; 
    }

}
@media (max-width: 509px) {
    .logo{
         width: auto;
         padding: 20;
    }
}

</style>