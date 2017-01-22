## WebUploader修改图片 ##
WebUploader为BAIDU FEX团队开源的文件图片上传插件，支持移动端的调用，使用起来效果不错。但对于图片上传后，上传修改的问题没有解决方案。恰好一项目中需要使用，于是研究如下。
基本思路为：当为编辑页面时，写一edit方法，在fileList的层中，添加初始化我们已经上传的图片。
### 初始化编辑函数 ###

    function edit(poster){
             $li = $( '<li id="editimage">' +
                     '<p class="title">文件名</p>' +
                     '<p class="imgWrap">'+
                     '</p>'+
                     '<p class="progress"><span></span></p>' +
                     '</li>' );
 	
 		    $btns = $('<div class="file-panel">' +
 		        '<span class="cancel">删除</span>' +
 		        '<span class="rotateRight">向右旋转</span>' +
 		        '<span class="rotateLeft">向左旋转</span></div>').appendTo( $li );
 		    $prgress = $li.find('p.progress span');
 		    $imgwrap = $li.find( 'p.imgWrap' );
 		    $info = $('<p class="error"></p>');
 		    $imgwrap.append("<img width='100%' height='100%' src='"+poster+"'/>");
 		    
 	        $wrap.find(".placeholder").addClass("element-invisible");
 	        $wrap.find(".statusBar").show();
 	        $wrap.find(".filelist").append($li); 
 	        $(".webuploader-pick").html("重新上传");
         }

### 调用初始化函数 ###

    if("1"===isEdit){
        	 edit(poster);  
        }

### 重新上传时移除原有图片 ###

    function modifyImage(){
         	$("#editimage").remove();
         }