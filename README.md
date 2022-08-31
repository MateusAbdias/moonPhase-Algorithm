# moonPhase-Algorithm 
### Algorithm for Calculating the Moon Phase in JavaScript :new_moon::moon:
Algorithm in JS developed by: Mateus Abdias

The formula used was made by: John Conway

Learn more: https://thiagovespa.com.br/blog/2018/04/05/como-saber-a-fase-da-lua-de-cabeca/

~~~ JavaScript
function main(number) {
    if (number >= 0 && number <= 1 ) {
        console.log("New Moon");
    } 
    else if (number >= 2 && number <= 6) {
        console.log("Waxing Crescent Moon");
    } 
    else if (number >= 7 && number <= 8) {
        console.log("First Quarter Moon");
    }
    else if (number >= 9 && number <= 13) {
        console.log("Waxing Gibbous Moon");
    }
    else if (number >= 14 && number <= 16) {
        console.log("Full Moon");
    }
    else if (number >= 17 && number <= 21) {
        console.log("Waning Gibbous Moon");
    }
    else if (number >= 22 && number <= 23) {
        console.log("Last Quarter Moon");
    }
    else if (number >= 24 && number <= 28) {
        console.log("Waning Crescent Moon");
    } 
    else {
        main(number - 28);
    }
};

//Function the moon-phase calculation
const moonPhaseCalculation = () => {
    let date = new Date;

    const year = date.getFullYear().toString();
    const today = date.getDate();
    let month = date.getMonth() + 1;
    //If it's January or February, add 2
    if (month === 1 || month === 2){
        month += 2;
    };

    //In the calculation, it uses only the last two digits of the year, and to do this I applied the slice method
    const yearSlice = year.slice(2);
    const yearNumber = parseInt(yearSlice);

    const yearformula = ((((yearNumber % 19 ) * 11) % 30) -8 ) % 30;
    //For the calculation formula for the year:
    //Take the remainder of the division by 19
    //Multiply by 11
    //Take the remainder of the division by 30
    //Since we are in the 21st century, subtract 8
    //And finally, take again the remainder of the division by 30

    const phaseNumber = yearformula + today + month; 
    //To calculate the moon phase formula, add the result of this expression (yearNumber) with the day and month

    return phaseNumber;
    //A value between 1 to 29 will be returned.
}

main(moonPhaseCalculation());
//Calling this function will cause the number returned to fall into one of the if of the main function

//And, if the number returned (phaseNumber) is 29, it will fall into the else that subtracts 28 from it, 
//that is, if the calculation phaseNumber returns 29 it is a new moon
~~~

