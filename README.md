# ds-code
function db_su_highlight_odr(odr,sock) {
	if(sock === undefined || sock ===0 || odr.length ===0) return;
	var parent = $('#ds-panel-center');
	var st = parent.scrollTop(), ph= parent.height()/2;
	var pos = st + odr.offset().top + odr.height()/2 - ph - parent.offset().top;
	var hg = st + ph;
	st = st - ph;
	if(gUserSetting['enable_notify_scroll'] && (pos < st || pos > hg)){
	    FnQueue.add(function(){
			parent.animate({ scrollTop: pos}, 500, function() {
				odr.removeClass('glisture');
			});
			setTimeout(function() {
				odr.removeClass('glisture');
			},1000);
		});
	}else{
		odr.addClass('glisture');
		setTimeout(function() {
			odr.removeClass('glisture');
		},1000); 
	}
}
