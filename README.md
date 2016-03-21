# 个人 sublime-snippet
## 安装方法
将src中文件放入
c:\Users\wxh\AppData\Roaming\Sublime Text 3\Packages\User\

## 使用

- fish-popup

		<div class="ui-dialog dialog-md">
		    <div class="modal-header">
		        <h4 class="modal-title">标题</h4>
		    </div>
		    <div class="modal-body">

		    </div>
		    <div class="modal-footer">
		        <button type="button" class="btn btn-default" data-dismiss>取消</button>
		        <button type="button" class="btn btn-primary js-ok">确定</button>
		    </div>
		</div>


- fish-popup-js

      define(['hbs!TemplateName'], function (template) {
      	var tag = 'ViewName';
      	var ViewName = fish.View.extend({
      		el:false,
      		template: template,
      		events: {
      			"click .js-ok": "ok"
      		},

      		initialize: function(options) {
      			console.log(tag, '--------initialize---------');
      		},

              beforeRender: function () {
                  console.log(tag, '--------beforeRender--------');
              },

      		afterRender: function() {
                  console.log(tag, '--------afterRender--------');
      		},

              remove: function () {
                  console.log(tag, '--------remove--------');
              },	

      		ok: function() {
      			this.popup.close("selrows");
      		}         			
      	});
      	return ViewName;
      });

      fish.popupView({
      	url: "treeView01/views/dialog/DlgFileUpload",
      	viewOption:{},
      	callback: function(popup,view) {
      		console.log("OK");
      	},
      	close: function(msg) {
      		console.log("return value: " + msg);
      	}
      })	

- fish-view-js

      define([
      	'hbs!TemplateName'
      ], function (template) {
      	var tag = 'ViewName';
      	var ViewName = fish.View.extend({
      		el:false,
      		template: template,
      		events: {
      		},

      		initialize: function(options) {
      			console.log(tag, '--------initialize---------');
      		},

              beforeRender: function () {
                  console.log(tag, '--------beforeRender--------');
              },

      		afterRender: function() {
                  console.log(tag, '--------afterRender--------');
      		},

              remove: function () {
                  console.log(tag, '--------remove--------');
              },				
      	});
      	return ViewName;
      });

- fish-tabs

      <div class="js-name-tab">
        <!-- Nav tabs -->
          <ul>
             <li>
                 <a href="#tabs-a">First</a>
              </li> 
               <li>
                   <a href="#tabs-b">Second</a>
              </li> 
          </ul>
          <!-- Tab panes -->
          <div id="tabs-a">
          </div>
          <div id="tabs-b">
          </div>
      </div>

- fish-js-tabs

      $(function() {
          var $tabs = $(".js-name-tab").tabs({
              activate: function(event, ui) { //tabActive的事件
                  var id = ui.newPanel.attr('id');
                  switch (id) {
                      case "tabs-a":
                          fish.info("tabs-a"); 
                          //this.requireView({url: "xxxx",selector: "#tabs-a"});                            
                          break;
                      case "tabs-b":
                          fish.info("tabs-b");
                          //this.requireView({url: "xxxx",selector: "#tabs-b"});                
                          break; 
                  }
              }
          });

          $tabs.tabs("option", "active", 0);  
      })
