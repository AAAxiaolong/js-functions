# js-functions

//获取随机颜色
	function getRandomColor(){
		//return "#"+("00000"+((Math.random()*16777215)>>0).toString(16)).slice(-6); 
		//随机生成暖色调颜色
		return "#"+('0'+((Math.random()*136+119)>>0).toString(16)).slice(-2)+('0'+((Math.random()*136+119)>>0).toString(16)).slice(-2)+('0'+((Math.random()*136+119)>>0).toString(16)).slice(-2);
	}
  
  /*格式化数字格式
	number	必需。要格式化的数字。如果未设置其他参数，则数字会被格式化为不带小数点且以逗号（,）作为千位分隔符。
	decimals	可选。规定多少个小数。如果设置了该参数，则使用点号（.）作为小数点来格式化数字。
	decimalpoint	可选。规定用作小数点的字符串。
	separator	可选。规定用作千位分隔符的字符串。仅使用该参数的第一个字符。比如 "xxx" 仅输出 "x"。
	注释：如果设置了该参数，那么所有其他参数都是必需的。
	*/
	function number_format(number){
        number = arguments[1]!=undefined ? parseFloat(number).toFixed(arguments[1])+'' : number+'';
        var isFloat = number.indexOf('.'),//是否为浮点数
            numLength = number.length,//数字长度
            intLength = isFloat>=0 ? isFloat : numLength,//整数部分长度
            intIndex = intLength-1,//整数部分索引长度
            forLength = Math.ceil(intLength/3),
            firstThousandsLength = intLength%3,//千分位最前边的个数
            arr=[],i,
            pointStr = arguments[2]!=undefined ? arguments[2] : '.';
            numArr = isFloat>=0 ? number.split(".") : ['',''];
            thousandsStr = arguments[3]!=undefined ? arguments[3].substr(0,1) : ',';
        for (i = 0; i < forLength; i++) {
            if(i==0 && firstThousandsLength<=0){
                arr.push(number.substr(0,3));
            }else if (i==0 && firstThousandsLength>0) {
                arr.push(number.substr(0,firstThousandsLength));
            }else if(firstThousandsLength>0){
                arr.push(number.substr((firstThousandsLength+3*(i-1)),3));
            }else{
                arr.push(number.substr(3*i,3));
            }
        };
        return isFloat>=0 ? arr.join(thousandsStr)+pointStr+numArr[1] : arr.join(thousandsStr);
    }
    
    
    /*
	*	string	必需。规定被检查的字符串。
	*	substring	必需。规定要搜索的字符串。
	*	start	可选。规定在字符串中何处开始搜索。
	*	length	可选。规定搜索的长度。
    */
  function substr_count(string,substring){
    	var str = string;
    	if (arguments[2]!=undefined) {
    		str = str.substr(arguments[2]);
    	};
    	if (arguments[3]!=undefined) {
    		str = str.substr(0,arguments[2]);
    	};
	    var res = str.match(eval('/'+substring+'/g'));
	    return res && res[0]!=='' ? res.length : 0;
	}
    
