МІНІСТЕРСТВО ОСВІТИ І НАУКИ УКРАЇНИ

Національний аерокосмічний університет ім. М. Є. Жуковського

«Харківський авіаційний інститут»

факультет програмної інженерії та бізнесу

кафедра інженерії програмного забезпечення

# ПРАКТИЧНА РОБОТА

з дисципліни « Об’єктно орієнтоване програмування »

на тему: « LINQ »

Виконав: студент 2 курсу групи № 623П

освітньої програми

121 інженерія програмного забезпечення

Заря М.С.

Прийняв: к.т.н. Лучшев П.О.

Харків – 2024

# ПОСТАНОВКА ЗАВДАННЯ

1. Скопіювати віддалений репозиторій (зробити Fork) за наданим посиланням у власний акаунт на GitHub: <https://github.com/IlonaShevchenko/Practice_Linq_2024>
2. Клонувати отриманий fork-репозиторій на власний комп’ютер.
3. Перевірити, що склонований проєкт запускається і виводить на екран тестове значення 13049.
4. Ознайомитися зі структурою проєкту.
5. Необхідно реалізувати методи Query1(), Query2(), …, Query10(), а саме: за допомогою мови LINQ реалізувати запити, формулювання яких оформлені у вигляді коментарів до кожного методу. Крім запиту мовою LINQ у кожному методі має бути реалізований вивід на екран результатів запиту.
6. Після реалізації кожного методу QueryN() необхідно робити commit, вказуючи номер N реалізованого запиту.
7. Оформити Readme.md файл

# ПОРЯДОК ВИКОНАННЯ РОБОТИ

Було скопійовано віддалений репозиторій із завданням, після чого було послідовно реалізовано 10 запитів. Далі наведено формулювання та реалізацію цих запитів.

**Запит №1** – Необхідно вивести всі матчі, які відбулися в Україні у 2012 році.

Реалізація:

static void Query1(List&lt;FootballGame&gt; games)

{

//Query 1: Вивести всі матчі, які відбулися в Україні у 2012 році.

var selectedGames = games.Where(g => g.Country == "Ukraine" && g.Date.Year == 2012); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 1 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames)

{

Console.WriteLine($"{game.Date.ToShortDateString()} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

}

**Запит №2** – Необхідно вивести Friendly матчі збірної Італії, які вона провела з 2020 року.

Реалізація:

static void Query2(List&lt;FootballGame&gt; games)

{

//Query 2: Вивести Friendly матчі збірної Італії, які вона провела з 2020 року.

var selectedGames = games.Where(g => g.Tournament == "Friendly" && (g.Away_team == "Italy" || g.Home_team == "Italy") && g.Date.Year >= 2020); // Корегуємо запит

// Перевірка

Console.WriteLine("\\n======================== QUERY 2 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames)

{

Console.WriteLine($"{game.Date.ToShortDateString()} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

}

**Запит №3** – Необхідно вивести всі домашні матчі збірної Франції за 2021 рік, де вона зіграла у нічию.

Реалізація:

static void Query3(List&lt;FootballGame&gt; games)

{

//Query 3: Вивести всі домашні матчі збірної Франції за 2021 рік, де вона зіграла у нічию.

var selectedGames = games.Where(g => g.Country == "France" && g.Away_score == g.Home_score && g.Date.Year == 2021); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 3 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames){

Console.WriteLine($"{game.Date.ToShortDateString()} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}"); }

}

**Запит №4** – Необхідно вивести всі матчі збірної Германії з 2018 року по 2020 рік (включно), в яких вона на виїзді програла.

Реалізація:

static void Query4(List&lt;FootballGame&gt; games)

{

//Query 4: Вивести всі матчі збірної Германії з 2018 року по 2020 рік (включно), в яких вона на виїзді програла.

var selectedGames = games.Where(g =>g.Away_team == "Germany" && g.Away_score &lt; g.Home_score && g.Date.Year &gt;= 2018 && g.Date.Year <= 2020); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 4 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames)

{

Console.WriteLine($"{game.Date.ToShortDateString()} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

}

**Запит №5** – Необхідно вивести всі кваліфікаційні матчі (UEFA Euro qualification), які відбулися у Києві чи у Харкові, а також за умови перемоги української збірної.

Реалізація:

static void Query5(List&lt;FootballGame&gt; games)

{

//Query 5: Вивести всі кваліфікаційні матчі (UEFA Euro qualification), які відбулися у Києві чи у Харкові, а також за умови перемоги української збірної.

var selectedGames = games.Where(g => g.Tournament == "UEFA Euro qualification" && (g.City == "Kharkiv" || g.City == "Kyiv") && g.Home_team == "Ukraine" && g.Home_score > g.Away_score ); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 5 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames)

{

Console.WriteLine($"{game.Date.ToShortDateString()} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

}

**Запит №6** – Необхідно вивести всі матчі останнього чемпіоната світу з футболу (FIFA World Cup), починаючи з чвертьфіналів (тобто останні 8 матчів).

Реалізація:

static void Query6(List&lt;FootballGame&gt; games)

{

//Query 6: Вивести всі матчі останнього чемпіоната світу з футболу (FIFA World Cup), починаючи з чвертьфіналів (тобто останні 8 матчів).

//Матчі мають відображатися від фіналу до чвертьфіналів (тобто у зворотній послідовності).

var selectedGames = games.Where(g => g.Tournament == "FIFA World Cup" && g.Date.Year == 2022).OrderByDescending(g => g.Date).Take(8); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 6 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames)

{

Console.WriteLine($"{game.Date.ToShortDateString()} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

}

**Запит №7** – Необхідно вивести перший матч у 2023 році, в якому збірна України виграла.

Реалізація:

static void Query7(List&lt;FootballGame&gt; games)

{

//Query 7: Вивести перший матч у 2023 році, в якому збірна України виграла.

FootballGame g = games.Where(g => g.Date.Year == 2023).OrderBy(g => g.Date).First(g => (g.Away_team == "Ukraine" && g.Away_score>g.Home_score) || (g.Home_team == "Ukraine" && g.Away_score < g.Home_score)); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 7 ========================");

// див. приклад як має бути виведено:

Console.WriteLine($"{g.Date.ToShortDateString()} {g.Home_team} - {g.Away_team}, Score: {g.Home_score} - {g.Away_score}, Country: {g.Country}");

}

**Запит №8** – Необхідно перетворити всі матчі Євро-2012 (UEFA Euro), які відбулися в Україні, на матчі з наступними властивостями: MatchYear - рік матчу, Team1 - назва приймаючої команди, Team2 - назва гостьової команди, Goals - сума всіх голів за матч

Реалізація:

static void Query8(List&lt;FootballGame&gt; games)

{

//Query 8: Перетворити всі матчі Євро-2012 (UEFA Euro), які відбулися в Україні, на матчі з наступними властивостями:

// MatchYear - рік матчу, Team1 - назва приймаючої команди, Team2 - назва гостьової команди, Goals - сума всіх голів за матч

var selectedGames = games.Where(g => g.Date.Year == 2012 && g.Tournament == "UEFA Euro" && g.Country == "Ukraine").Select(g => new {

MatchYear = g.Date.Year,

Team1 = g.Home_team,

Team2 = g.Away_team,

Goals = g.Away_score + g.Home_score,

}); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 8 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames)

{

Console.WriteLine($"{game.MatchYear} {game.Team1} - {game.Team2}, Goals: {game.Goals}");

}

}

**Запит №9** – Необхідно перетворити всі матчі UEFA Nations League у 2023 році на матчі з наступними властивостями:. MatchYear - рік матчу, Game - назви обох команд через дефіс (першою - Home_team), Result - результат для першої команди (Win, Loss, Draw)

Реалізація:

static void Query9(List&lt;FootballGame&gt; games)

{

//Query 9: Перетворити всі матчі UEFA Nations League у 2023 році на матчі з наступними властивостями:

// MatchYear - рік матчу, Game - назви обох команд через дефіс (першою - Home_team), Result - результат для першої команди (Win, Loss, Draw)

var selectedGames = games.Where(g => g.Date.Year == 2023&& g.Tournament == "UEFA Nations League").Select(g => new

{

MatchYear = g.Date.Year,

Game = $"{g.Home_team}-{g.Away_team}",

Result = (g.Home_score>g.Away_score)?"Win": (g.Home_score < g.Away_score)?"Loss":"Draw"

}); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 9 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames)

{

Console.WriteLine($"{game.MatchYear} {game.Game}, Result for team1: {game.Result}");

}

}

**Запит №10** – Необхідно вивести з 5-го по 10-тий (включно) матчі Gold Cup, які відбулися у липні 2023 р0.

Реалізація:

static void Query10(List&lt;FootballGame&gt; games)

{

//Query 10: Вивести з 5-го по 10-тий (включно) матчі Gold Cup, які відбулися у липні 2023 р.

var selectedGames = games.Where(g => g.Date.Year == 2023 && g.Date.Month == 7 && g.Tournament == "Gold Cup").Take(10).Skip(4); // Корегуємо запит !!!

// Перевірка

Console.WriteLine("\\n======================== QUERY 10 ========================");

// див. приклад як має бути виведено:

foreach (var game in selectedGames)

{

Console.WriteLine($"{game.Date.ToShortDateString()} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

}

# Висновки

Під час виконання практичної роботи було реалізовано мовою LINQ методи для виконання 10 запитів. Для цього було зроблено на своїй сторінці Github копію віддаленого репозиторію, після чого з копії було витягнуто файли шаблону проекту. Після ознайомлення зі структурою проекту, було реалізовано з використанням методів розширення LINQ виконання 10 запитів. Було проведено порівняння фактичних результатів з очікуваними, після чого було зроблено висновку, що запити реалізовано коректно.

