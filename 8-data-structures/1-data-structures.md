# Data Structures
Data structures are collection of values, the relationship between them and the functions or the operations that can be applied to the data.

## ES2015 Classes
```javascript
class Student {
    static count = 0;
    // ES6 Does'nt support static properties :(.Only Chrome console does
    constructor(firstname, lastname, year) {
        this.firstname = firstname;
        this.lastname = lastname;
        this.grade = year;
        this.scores = [];
        Student.count++;
    }
    fullName() {
        return `${this.firstname} ${this.lastname}`;
    }
    addScore(score) {
        this.scores.push(score);
    }
    averageScore() {
        let sum = this.scores.reduce((acc, val) => acc + val);
        return sum / this.scores.length;
    }
}

let emily = new Student("Emily", "Wolowitz");
// grade remains undefined as we don't provide it

emily.fullName()
// Emily Wolowitz

emily.addScore(92);
emily.addScore(90);
emily.scores;
// [92, 91]

emily.averageScore();
// 91
```