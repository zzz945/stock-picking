<!--客户程序必须加!important属性优先级强制重写,而且不能加scoped-->
<template>
    <div>
        <zpagenav :page="page" :page-size="pageSize" :total="total" :max-link="maxLink" :page-handler="pageHandler">
    </div>
</template>

<script>
export default {
  props: {
    page: Number,
    pageSize: Number,
    total: Number,
    maxLink: Number,
    pageHandler: Function
  }
}
</script>

<!--不能加scoped-->
<style lang="less">
    @import '../../../styles/variable.less';
    .sr-only {
        position: absolute;
        width: 1px;
        height: 1px;
        padding: 0;
        margin: -1px;
        overflow: hidden;
        clip: rect(0, 0, 0, 0);
        border: 0;
    }
    
    .sr-only-focusable:active,
    .sr-only-focusable:focus {
        position: static;
        width: auto;
        height: auto;
        margin: 0;
        overflow: visible;
        clip: auto;
    }
    
    .m-r-1 {
        margin-right: 1rem!important;
    }
    
    .pagination {
        display: inline-block;
        padding-left: 0;
        margin-top: 1rem;
        margin-bottom: 1rem;
        border-radius: .25rem;
        font-weight: bold;
        font-size: 18px;
    }
    
    .page-item {
        display: inline;
    }
    
    .page-item:first-child .page-link {
        margin-left: 0;
        border-top-left-radius: .25rem;
        border-bottom-left-radius: .25rem;
    }
    
    .page-item:last-child .page-link {
        border-top-right-radius: .25rem;
        border-bottom-right-radius: .25rem;
    }
    
    .page-item.active .page-link,
    .page-item.active .page-link:focus,
    .page-item.active .page-link:hover {
        z-index: 2;
        color: @theme-color-text;
        cursor: default;
        background-color: @theme-color-eye;
    }
    
    .page-item.disabled .page-link,
    .page-item.disabled .page-link:focus,
    .page-item.disabled .page-link:hover {
        color: @theme-color-disable;
        cursor: not-allowed;
        background-color: @theme-color;
    }
    
    .page-link {
        position: relative;
        float: left;
        padding: .5rem .75rem;
        margin-left: -1px;
        line-height: 1.5;
        color: @theme-color-text;
        text-decoration: none;
        background-color: @theme-color;
    }
    
    .page-link:focus,
    .page-link:hover {
        color: @theme-color-text;
        background-color: @theme-color;
    }
    
    .pagination-lg .page-link {
        padding: .75rem 1.5rem;
        font-size: 1.25rem;
        line-height: 1.333333;
    }
    
    .pagination-lg .page-item:first-child .page-link {
        border-top-left-radius: .3rem;
        border-bottom-left-radius: .3rem;
    }
    
    .pagination-lg .page-item:last-child .page-link {
        border-top-right-radius: .3rem;
        border-bottom-right-radius: .3rem;
    }
    
    .pagination-sm .page-link {
        padding: .275rem .75rem;
        font-size: .875rem;
        line-height: 1.5;
    }
    
    .pagination-sm .page-item:first-child .page-link {
        border-top-left-radius: .2rem;
        border-bottom-left-radius: .2rem;
    }
    
    .pagination-sm .page-item:last-child .page-link {
        border-top-right-radius: .2rem;
        border-bottom-right-radius: .2rem;
    }
    
    .pager {
        padding-left: 0;
        margin-top: 1rem;
        margin-bottom: 1rem;
        text-align: center;
        list-style: none;
    }
    
    .pager::after {
        display: table;
        clear: both;
        content: "";
    }
    
    .pager li {
        display: inline;
    }
    
    .pager li > a,
    .pager li > span {
        display: inline-block;
        padding: 5px 14px;
        background-color: #fff;
        border: 1px solid #ddd;
        border-radius: 15px;
    }
    
    .pager li > a:focus,
    .pager li > a:hover {
        text-decoration: none;
        background-color: #eceeef;
    }
    
    .pager .disabled > a,
    .pager .disabled > a:focus,
    .pager .disabled > a:hover {
        color: #818a91;
        cursor: not-allowed;
        background-color: #fff;
    }
    
    .pager .disabled > span {
        color: #818a91;
        cursor: not-allowed;
        background-color: #fff;
    }
    
    .pager-next > a,
    .pager-next > span {
        float: right;
    }
    
    .pager-prev > a,
    .pager-prev > span {
        float: left;
    }
</style>