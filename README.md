# bingo_algorithm

``` javascript
const sheet = [
  [false, true, false, false, false, false],
  [true, true, true, true, true, true],
  [false, true, false, true, false, false],
  [false, true, true, false, false, false],
  [false, true, false, false, false, false],
  [true, true, true, true, true, false],
];

const checkRow = (sheet) => {
  const reachRow = [];
  const bingoRow = [];
  sheet.map((row, index) => {
    const trueTmp = [];
    row.forEach((item) => {
      if (item === true) {
        trueTmp.push(true);
      }
    });
    if (trueTmp.length === 5) {
      reachRow.push(index);
    } else if (trueTmp.length === 6) {
      bingoRow.push(index);
    }
  });
  return [reachRow, bingoRow];
};

const checkColumn = (sheet) => {
  const reachCol = [];
  const bingoCol = [];
  const converted = [[], [], [], [], [], []];
  // ここで2次元配列の縦と横を組み替えてconvertedに入れている
  sheet.map((row, index) => {
    const tmp = [];
    row.forEach((item, index) => {
      converted[index].push(item);
    });
  });
  // ここまで
  converted.map((row, index) => {
    const trueTmp = [];
    row.forEach((item) => {
      if (item === true) {
        trueTmp.push(true);
      }
    });
    if (trueTmp.length === 5) {
      reachCol.push(index);
    } else if (trueTmp.length === 6) {
      bingoCol.push(index);
    }
  });
  return [reachCol, bingoCol];
};

const checkDiagonal = (sheet) => {
  const reachDiagonal = [];
  const bingoDiagonal = [];
  const converted = [
    // 一つ目が左斜め下
    [
      sheet[0][0],
      sheet[1][1],
      sheet[2][2],
      sheet[3][3],
      sheet[4][4],
      sheet[5][5],
    ],
    // 二つ目が右斜め下
    [
      sheet[0][5],
      sheet[1][4],
      sheet[2][3],
      sheet[3][2],
      sheet[4][1],
      sheet[5][0],
    ],
  ];
  converted.map((row, index) => {
    const trueTmp = [];
    row.forEach((item, index) => {
      if (item === true) {
        trueTmp.push(true);
      }
    });
    if (trueTmp.length === 5) {
      reachDiagonal.push(index);
    } else if (trueTmp.length === 6) {
      bingoDiagonal.push(index);
    }
  });

  return [reachDiagonal, bingoDiagonal];
};

const result = checkDiagonal(sheet);
const reachDiagonal = result[0];
const bingoDiagonal = result[1];
console.log(`reach ${reachDiagonal}`);
console.log(`bingo ${bingoDiagonal}`);

// const result = checkRow(sheet);
// const reachRow = result[0];
// const bingoRow = result[1];
// console.log(`reach ${reachRow}`);
// console.log(`bingo ${bingoRow}`);

// const result = checkColumn(sheet);
// const reachCol = result[0];
// const bingoCol = result[1];
// console.log(`reach ${reachCol}`);
// console.log(`bingo ${bingoCol}`);

```
