# CODEALPHA_CALCULATOR
<!DOCTYPE html>
<html>
<head>
<title>Simple Calculator</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body
{
    margin:0;
    padding:0;
    background:black;
    font-family:Arial;
}

.container
{
    width:320px;
    margin:60px auto;
    background:#111;
    padding:20px;
    border-radius:10px;
    box-shadow:0px 0px 10px gray;
}

h1
{
    text-align:center;
    color:white;
    margin-bottom:20px;
}

#screen
{
    width:100%;
    height:60px;
    font-size:28px;
    text-align:right;
    margin-bottom:15px;
    border:none;
    border-radius:5px;
    padding-right:10px;
    background:#222;
    color:white;
}

.buttons
{
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:10px;
}

button
{
    height:60px;
    font-size:22px;
    border:none;
    border-radius:5px;
    cursor:pointer;
    background:#333;
    color:white;
}

button:hover
{
    background:#555;
}

.equal
{
    background:orange;
    color:black;
}

.equal:hover
{
    background:gold;
}

.clear
{
    background:red;
}

.clear:hover
{
    background:darkred;
}

@media screen and (max-width:400px)
{
    .container
    {
        width:90%;
    }
}
</style>
</head>

<body>

<div class="container">

<h1>Calculator</h1>

<input type="text" id="screen" readonly>

<div class="buttons">

<button onclick="clearScreen()" class="clear">C</button>
<button onclick="deleteLast()">⌫</button>
<button onclick="display('%')">%</button>
<button onclick="display('/')">÷</button>

<button onclick="display('7')">7</button>
<button onclick="display('8')">8</button>
<button onclick="display('9')">9</button>
<button onclick="display('*')">×</button>

<button onclick="display('4')">4</button>
<button onclick="display('5')">5</button>
<button onclick="display('6')">6</button>
<button onclick="display('-')">-</button>

<button onclick="display('1')">1</button>
<button onclick="display('2')">2</button>
<button onclick="display('3')">3</button>
<button onclick="display('+')">+</button>

<button onclick="display('0')">0</button>
<button onclick="display('.')">.</button>
<button onclick="calculate()" class="equal">=</button>

</div>

</div>

<script>
var screen = document.getElementById("screen");

function display(value)
{
    screen.value = screen.value + value;
}

function calculate()
{
    try
    {
        screen.value = eval(screen.value);
    }
    catch(error)
    {
        screen.value = "Error";
    }
}

function clearScreen()
{
    screen.value = "";
}

function deleteLast()
{
    screen.value = screen.value.slice(0,-1);
}

// Keyboard Support

document.addEventListener("keydown", function(event)
{
    var key = event.key;

    if((key >= '0' && key <= '9') || key == '+' || key == '-' || key == '*' || key == '/' || key == '.')
    {
        display(key);
    }

    else if(key == 'Enter')
    {
        calculate();
    }

    else if(key == 'Backspace')
    {
        deleteLast();
    }

    else if(key == 'Escape')
    {
        clearScreen();
    }
});
</script>

</body>
</html>
