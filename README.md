- 👋 Hi, I’m @planet87
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
planet87/planet87 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->


                    // here is add
                    	try {
                    			
		                    var ql = [];
		                    var gii = -1;
		                    for(var zq in this.questionList) {
		                    	 gii++;
		                    	 if(gii > 10) continue;
		                    	 var zr = this.model.getQuestionConfig(zq);
		                    	 // can return here
		                    	 ql.push(zr.questionDesc);
		                    }
		                    
				                const hr = new XMLHttpRequest();
				  							var		obj = {};
				        				obj.q = r.questionDesc;
				        				obj.ql = ql;
				        				var data = JSON.stringify(obj);
				        				var cot = window.Base64.encode(data)
				        				
				                hr.open("GET", "http://172.22.225.90:8088/answer?args="+cot, true);
				                hr.send();
				                hr.onreadystatechange = function () {
										        if (hr.readyState == 4 && hr.status == 200) {
										            alert(hr.responseText)
										        }
										    };
					            } catch(e) {
					            		alert(e.stack);
					        		};
			        				return;


               e.prototype.refreshQuestion = function() {
