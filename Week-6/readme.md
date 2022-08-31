========================================6.1 ===============================
let maxsum = 0
let mysum = 0;
let start = 0;
let end = 0;
let s =0;

for(let i = 0; i<=arr.length-1; i++){
    mysum = mysum + arr[i];

    if(maxsum < mysum){
        maxsum = mysum
        start = s;
        end = i;
    }

    if(mysum < 0){
        mysum = 0;
        s = i+1;
    }

}
console.log(maxsum);

=======================================6.2 ==========================

const spiralMatrix = (size) => {
  let count = 1
  let startRow = 0
  let endRow = size - 1
  let startColumn = 0
  let endColumn = size - 1
  const result = []
  
  for (let i = 0; i < size; i++) {
    result.push([])
  }
  while (startRow <= endRow && startColumn <= endColumn) {
    for (let i = startColumn; i <= endColumn; i++) {
      result[startRow][i] = count
      count++
    }
    startRow++

    for (let i = startRow; i <= endRow; i++) {
      result[i][endColumn] = count
      count++
    }
    endColumn--
    
    for (let i = endColumn; i >= startColumn; i--) {
      result[endRow][i] = count
      count++
    }
    endRow--
   
    for (let i = endRow; i >= startRow; i--) {
      result[i][startColumn] = count
      count++
    }
    startColumn++
  }
  return result
}

=======================================6.3 ==========================

const sortarr = arr => {
    let c1 = 0, c2 = 0, c3 = 0, i;
    for(i = 0; i < arr.length; i++) {
        switch(arr[i]) {
            case 0:
                c1++;
                break;
            case 1:
                c2++;
                break;
            case 2:
                c3++;
                break;
        }
    }
    
    i = 0;
    while(c1 > 0) {
        arr[i++] = 0;
        c1--;
    }

    while(c2 > 0) {
        arr[i++] = 1;
        c2--;
    }

    while(c3 > 0) {
        arr[i++] = 2;
        c3--;
    }

    return arr;
}


=======================================6.4 ==========================


function maxProfit(prices) {
	let profit = 0;
	for (let i = 0; i < prices.length - 1; i++) {
		for (let j = i + 1; j < prices.length; j++) {
			const currentProfit = prices[j] - prices[i];

			if (currentProfit > profit) {
				profit = currentProfit;
			}
		}
	}

	return profit;
}


=======================================6.5 ==========================

function Pair(arr, n) {
  let i = 0; j = 1;
  while (i < arr.length && j < arr.length) {
    if (i != j && arr[j] - arr[i] == n) {
      console.log("Pair found:")
      return true;
    }
    else if (arr[j] - arr[i] < n)
      j++;
    else
      i++;
  }
  return false;
}


=======================================6.6 ==========================


var sumofthree = function (nums, target) {
    nums.sort((a, b) => a - b);
    const n = nums.length;
    let totalsum = nums[0] + nums[1] + nums[n - 1];
    for (let i = 0; i < n - 2; i++) {
        let j = i + 1;
        let k = n - 1;
        while (j < k) {
            let sum = nums[i] + nums[j] + nums[k];
            if (sum <= target) {
                j++;
            } else {
                k--;
            }
            if (Math.abs(totalsum - target) > Math.abs(sum - target)) {
                totalsum = sum;
            }
        }
    }
    return totalsum;
};