# web
menuClick: function (e, synthetic)
		{
			var target = jQuery(e.currentTarget)
			,	this_expander = target.next('[data-type="menu-tree-node-expander"]')
			, 	this_expander_is_opened = this_expander.hasClass('in')
			
			,	this_expandable = target.closest('[data-type="menu-tree-node-expandable"]')
			,	all_expandables = this.$('[data-type="menu-tree-node-expandable"]');

			all_expandables.removeClass('open');
			this_expandable.addClass('open');
			
			//if inside a closed expander: close others open this one
			var expanding_expander = this.$(target.data('target'));
			if (!this_expander_is_opened)
			{
				var open_expanders = this.$('[data-type="menu-tree-node-expander"].in');
				
				jQuery.fn.collapse.call(open_expanders, 'hide');
				jQuery.fn.collapse.call(expanding_expander, 'show');
			}
