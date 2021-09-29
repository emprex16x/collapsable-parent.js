# collapsable-parent.js

``` html

<hr class="collapse-parent__line" data-title="описание">

```

``` js
	function collapseParent(){

		let _this = $(this);

		if(!_this.parent().is('.collapsable-parent__container')){
			_this.parent()
			.wrapInner('<div class="collapsable-parent__container">')
			.wrapInner('<div class="collapsable-parent">')
			.css('position', 'relative');
			_this.parent().parent().append('<button class="collapsable-parent__btn"> Развернуть '+_this.data('title'));
		}

		_this.parent().css({'overflow': 'hidden', 'height': _this.position().top});

	}
	
	$(window).resize(function(){$('hr.collapse-parent__line').each(collapseParent)}).trigger('resize');

	$(document).on('click', '.collapsable-parent__btn', function(){
		$(this).toggleClass('collapsed');
		if(!$(this).is('.collapsed')){
			$(this).text('Развернуть '+ $(this).parent().find('.collapse-parent__line').data('title'));
			$(this).parent().children('.collapsable-parent__container')
			.css({'overflow': 'hidden', 'height': $(this).parent().find('.collapse-parent__line').position().top});
		}else{
			$(this).text('Свернуть '+ $(this).parent().find('.collapse-parent__line').data('title'));
			$(this).parent().children('.collapsable-parent__container').css('height', '');
		}
	});
```
