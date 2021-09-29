# collapsable-parent.js

example

``` html
<p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. 
<hr class="collapse-parent__line" data-title="описание"> 
It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. </p>

```

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
