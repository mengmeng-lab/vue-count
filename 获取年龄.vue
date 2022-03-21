// 获取年龄
getAge(card) {
  var len = card.length;
  if (len == 0) {
      return 0;
  } else {
      if ((len != 15) && (len != 18)) //身份证号码只能为15位或18位其它不合法
      {
          return 0;
      }
  }
  var strBirthday = "";
  if (len == 18) { //处理18位的身份证号码从号码中得到生日和性别代码
      strBirthday = card.substr(6, 4) + "/" + card.substr(10, 2) + "/" + card.substr(12, 2);
  }
  if (len == 15) {
      strBirthday = "19" + card.slice(6,12)
      strBirthday = strBirthday.replace(/(.{4})(.{2})/,"$1/$2/");
  }
  // 时间字符串里，必须是 "/"
  var birthDate = new Date(strBirthday);
  var nowDateTime = new Date();
  var age = nowDateTime.getFullYear() - birthDate.getFullYear();
  // 再考虑月、天的因素;.getMonth()获取的是从0开始的，这里进行比较，不需要加1
  if (nowDateTime.getMonth() < birthDate.getMonth() || (nowDateTime.getMonth() == birthDate.getMonth() && nowDateTime.getDate() < birthDate.getDate())) {
      age--;
  }
  return age;
},
