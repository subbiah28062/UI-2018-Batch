1)does sum of any two numbers in the array returns 8

    const months = [7,3,4,4];

    const sada = !!months.find((mon, monIndex) =>
        months.find((mont, montIndex) => montIndex !== monIndex && (mon + mont) === 8));

    console.log(sada); //true

2)Find longest sequency of matching string in s1 and s2.
    const s1 = 'AGGTAB';
    const s2 = 'GXTXAYB';

    const s1Split = [...s1];
    let longest = '';

    s1Split.find((s1Str, s1StrIndex) => {
    let s2Str = [...s2];
    const s1Array = s1Split.slice(s1StrIndex).filter((s1SubStr, s1SubStrIndex) => {
        const Index = s2Str.findIndex((s2SubStr) => s2SubStr === s1SubStr);
        if(Index !== -1) {
        s2Str.splice(0, Index+1);
        }
        return Index !== -1;
    });
    if(s1Array.length > [...longest].length ) {
        longest = s1Array.join('');
    }
    return [...longest].length >= s1.slice(s1StrIndex+1).length;
    });

    console.log(longest); //GTAB

3)returning infinite number of function if called with value;

    const sum = a => b => b ? sum(a+b) : a;

    console.log(sum(1)(2)(3)()); //6

4)lodash isEqual 

const findType = (arg1, arg2) => {
  const arg1Type = arg1 && Array.isArray(arg1) ? 'Array': typeof arg1;
  const arg2Type = arg2 && Array.isArray(arg2) ? 'Array': typeof arg2;
  return ( arg1Type && arg2Type && arg1Type === arg2Type ) ? arg1Type : undefined;
}
const isEqual = (arg1, arg2) => {
  switch (findType(arg1, arg2)) {
    case 'Array': {
      return arg1.length === arg2.length && !arg1.find((arr, arrIndex) => !isEqual(arr, arg2[arrIndex]));
    }
    case 'number':
    case 'string':
    case 'boolean': {
      return arg1 === arg2;
    }
    case 'object': {
      const obj1 = Object.entries(arg1);
      const obj2 = Object.entries(arg2);
      return isEqual(obj1, obj2);
    }
    case 'function': {
      return arg1.toString() == arg2.toString()  
    }
    default: {
      return false;
    }
  }
}

console.log(isEqual([{a:90, b:90, c:[1,2,3]},2], [{a:90, b:90,c:[1,2,3]},2]));
console.log(isEqual(() => { console.log('a')}, () => { console.log('a')}));


5) Easing function

// t = current time
// b = start value
// c = change in value (final value - start value)
// d = total duration
const linear = (t, b, c, d) => {
	t/=d;
	return b+c*(t);
}

const quiticBeizer = (t, b, c, d) => {
	const ts=(t/=d)*t;
	const tc=ts*t;
	return b+c*(-2*ts*ts + 10*tc + -15*ts + 8*t);
}

const easeOutElastic = (elapsed, initialValue, amountOfChange, duration) => {
	let s = 1.70158;
	let p = 0;
	let a = amountOfChange;
	if (elapsed === 0) {
		return initialValue;
	}
	if ((elapsed /= duration) === 1) {
		return initialValue + amountOfChange;
	}
	if (!p) {
		p = duration * 0.3;
	}
	if (a < Math.abs(amountOfChange)) {
		a = amountOfChange;
		s = p / 4;
	} else {
		s = p / (2 * Math.PI) * Math.asin(amountOfChange / a);
	}
	return a * Math.pow(2, -10 * elapsed) * Math.sin((elapsed * duration - s) * (2 * Math.PI) / p) + amountOfChange + initialValue;
}

const easing = async (b, e, d, steps ,t) => {
  t = t || steps || 1;
  const currentStep = easeOutElastic(t, b, e - b, d );
  await setTimeout(() => true, (steps || 1));
  console.log(currentStep)
  t = t + (steps || 1);
  if(t <= d) {
    easing(b, e, d, steps, t)
  }else {
    console.log(e)
  }
}

easing(0, 100, 1000, 10);



6)//This 

class thisExample {
  	data = 1 // equivalent to this.data = 1; property of thisExample;
    arrow = () => {
      console.log('arrow', this.data) // this refers to thisExample
    }
    doubleArrow = () => () => {
      console.log('d', this.data) // this refers to thisExample
    }
    e() {
      console.log('e', this.data) // this refers to thisExample
      const ee = () => {
        console.log('ee', this.data) // this refers to this of e which is thisExample
      }
      ee()
      const ee2 = function() {
        console.log('ee2e', this) // this refers to e which is not an object so its undefined
        const ee2e = () => {
          console.log('ee2e', this) // this refers to this of ee2 which is e which is not an object so its undefined
        }
        ee2e()
      }
      ee2()
    }
}

const ThisExample = new thisExample;

ThisExample.e();



7) Elevation problem


function findHighPoints(elevations) {
    const rows = elevations[0];
    const columns = elevations[1];
    const noOfArea = rows * columns;
    elevations.splice(0, 2);
    const listOfEle = elevations.map((area, areaI) => {
        const currentRow = Math.floor(areaI/columns);
        const currentColumn = areaI - (currentRow * columns);
        let BigElevation = true;
        Array.from({length: rows}).forEach((rowD, row) => {
            if(BigElevation && [currentRow - 1, currentRow, currentRow +1].includes(row)) {
                Array.from({length: columns}).forEach((columnD, column) => {
                    if(BigElevation && [currentColumn - 1, currentColumn, currentColumn +1].includes(column)){
                      if(!(currentRow === row && currentColumn === column)){
                          BigElevation = area > elevations[(row * columns) +column];
                      }
                    }
                });
            }
        });
        return BigElevation;
    });
  
  
    const splitGrp = (array, cols) => {
        const split = (array, cols) => {
            if (cols == 1) return array;
            let size = Math.floor(array.length / cols);
            return array.slice(0, size).concat([null]).concat(split(array.slice(size), cols - 1));
        }
        const splitWithNull = split(array, cols);
        let groups = [], group = [];
        splitWithNull.forEach((spl) => {
            if (spl === null) {
                groups.push(group);
                group = [];
            } else {
                group.push(spl);
            }
        });
        groups.push(group);
        return groups.filter(grp => grp.length > 0);
    }
    return splitGrp(listOfEle, columns)
}

const asd = [4
,4
,1,2,4,9
,1,5,3,6
,2,2,3,5
,3,6,2,4]
console.log(findHighPoints(asd))


8) sum of fractions

    const getSum = (num: number): number => {
      let sum: number = 0;
      let deno: number;
      Array(num)
        .fill(0)
        .forEach(() => {
          deno = deno ? deno + 3 : 1;
          sum += 1 / deno;
        });
      return sum;
    };
    console.log("getsum", getSum(6).toFixed(2));