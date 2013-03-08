#title1
text  
text2 :

	function(req, res){
	  var start_time = Date.now();
	  myquery("SELECT * FROM verycd WHERE del_flag = 0 AND verycdid = '"+req.params.id+"'; "
	  	, function (rows) {
	  		if (rows.length == 1){
	  			rows[0]["starttime"] = start_time;
	  			res.render('topic',rows[0]);
	  			//res.json(rows[0]);
	  		}else{
	  			res.redirect('/404');
	  		}
	  	}, DBCACHESECOND) //myquery("SELECT * FROM verycd WHERE del_flag = 0 AND verycdid = '"+req.params.id+"'; "
	},
		
