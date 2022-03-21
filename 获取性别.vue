// 获取性别
getSex(card) {
  var sexStr = '';
  if (parseInt(card.slice(-2, -1)) % 2 == 1) {
    sexStr = '男';
  } else {
    sexStr = '女';
  }
  return sexStr;
},
