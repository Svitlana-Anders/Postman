{
	"info": {
		"_postman_id": "3e964937-3247-4389-8d53-e723a9b63393",
		"name": "HW_2",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
		"_exporter_id": "20553074"
	},
	"item": [
		{
			"name": "first",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"pm.test(\"Body matches correctly string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"This is the first responce from server!ss\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{url_1}}/first",
					"host": [
						"{{url_1}}"
					],
					"path": [
						"first"
					]
				}
			},
			"response": []
		},
		{
			"name": "login",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"var jsonData = pm.response.json();\r",
							"\r",
							"var resp_token = jsonData.token\r",
							"console.log(resp_token)\r",
							"\r",
							"pm.environment.set(\"token\", resp_token);"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "formdata",
					"formdata": [
						{
							"key": "login",
							"value": "Vadim ",
							"type": "text"
						},
						{
							"key": "password",
							"value": "sdavdfvfv",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{url_1}}/login",
					"host": [
						"{{url_1}}"
					],
					"path": [
						"login"
					]
				}
			},
			"response": []
		},
		{
			"name": "user_info_3",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							" var resp_Data = pm.response.json();  //распарсили ответ\r",
							"\r",
							"var name = resp_Data.name     //объявила переменную name из распарсенного jsona\r",
							"pm.test(\"Response name\", function () {  //поверить, что...\r",
							"  pm.expect(resp_Data.name).to.eql(\"Anna\"); // сравнила имя в ответе с заданным \"Анна\"  \r",
							"});\r",
							"    \r",
							"\r",
							"var age = resp_Data.age //объявила перенменную age из распарсенного jsona\r",
							"pm.test(\"Response age\", function () {  //поверить, что...\r",
							"    pm.expect(resp_Data.age).to.eql(\"25\"); //сравнила возраст в ответе с заданным \"25\"\r",
							"    });\r",
							"\r",
							"var salary = resp_Data.salary //объявила перенменную salary из распарсенного jsona\r",
							"pm.test(\"Response salary\", function () {  //поверить, что...\r",
							"    pm.expect(resp_Data.salary).to.eql(1000); //сравнила salary в ответе с заданным  1000\r",
							"  });\r",
							"\r",
							"console.log(name) //вывела значение переменной в консоль\r",
							"console.log(age)\r",
							"console.log(salary)\r",
							"\r",
							"var req_Data = request.data; //распарсила данные из запроса\r",
							"\r",
							"var req_name = req_Data.name //объявила переменную name из запроса\r",
							"pm.test(\"name from request\", function () { //проверить что....\r",
							"   pm.expect(resp_Data.name).to.eql(req_name); //сравнила name из ответа  c name  из запроса\r",
							"});\r",
							"\r",
							"var req_age = req_Data.age //объявила переменную age из запроса\r",
							"pm.test(\"age from request\", function () {  //проверить что....\r",
							"   pm.expect(resp_Data.age).to.eql(req_age); //сравнила age из ответа  c age  из запроса\r",
							"});\r",
							"\r",
							"var req_salary = +req_Data.salary //объявила переменную age из запроса\r",
							"pm.test(\"salary from request\", function () {  //проверить что....\r",
							"   pm.expect(resp_Data.salary).to.eql(req_salary); //сравнила age из ответа  c age  из запроса\r",
							"});\r",
							"\r",
							"var family = resp_Data.family\r",
							"console.log(family)\r",
							"\r",
							"var u_salary_resp = +resp_Data.family.u_salary_1_5_year //объявила переменную u_salary из ответа\r",
							"\r",
							"pm.test(\"u_salary from response\", function () {  //проверить что....\r",
							"   pm.expect(resp_Data.family.u_salary_1_5_year).to.eql(req_salary*4); //сравнила зарплату из ответа      с зарплатой   из запроса, умноженной на 4\r",
							"});\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "formdata",
					"formdata": [
						{
							"key": "name",
							"value": "Anna",
							"type": "text"
						},
						{
							"key": "age",
							"value": "25",
							"type": "text"
						},
						{
							"key": "salary",
							"value": "1000",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{url_1}}/user_info_3",
					"host": [
						"{{url_1}}"
					],
					"path": [
						"user_info_3"
					]
				}
			},
			"response": []
		},
		{
			"name": "object_info_3",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"\r",
							" var resp_Data = pm.response.json();  //распарсили ответ\r",
							"var req_Data = pm.request.url.query.toObject() //распарсила данные из урла запроса\r",
							"\r",
							"var req_name = req_Data.name //объявила переменную name из запроса\r",
							"pm.test(\"name from request\", function () { //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.name).to.eql(req_name); //сравнила name из ответа  c name  из запроса\r",
							"});\r",
							"\r",
							"var req_age = req_Data.age //объявила переменную age из запроса\r",
							"pm.test(\"age from request\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.age).to.eql(req_age); //сравнила age из ответа  c age  из запроса\r",
							"});\r",
							"\r",
							"var req_salary = +req_Data.salary //объявила переменную age из запроса\r",
							"pm.test(\"salary from request\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.salary).to.eql(req_salary); //сравнила age из ответа  c age  из запроса\r",
							"});\r",
							"\r",
							"var family = resp_Data.family //объявила переменную family\r",
							"console.log(family)\r",
							"\r",
							"pm.test(\"Dog has name\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data.family.pets.dog).to.have.property(\"name\"); //параметр dog имеет name\r",
							"});\r",
							"pm.test(\"Dog has age\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data.family.pets.dog).to.have.property(\"age\"); //параметр dog имеет age\r",
							"});\r",
							"pm.test(\"Dogs name from resp\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data.family.pets.dog.name).to.eql(\"Luky\");//сравнила,что параметр name(в dog) равен luky\r",
							"});\r",
							"pm.test(\"Dogs name from resp\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data.family.pets.dog.age).to.eql(4); //сравнила, что параметр age(в dog) равен 4\r",
							"});\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{url_1}}/object_info_3?name=Ola&age=27&salary=2000",
					"host": [
						"{{url_1}}"
					],
					"path": [
						"object_info_3"
					],
					"query": [
						{
							"key": "name",
							"value": "Ola"
						},
						{
							"key": "age",
							"value": "27"
						},
						{
							"key": "salary",
							"value": "2000"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "object_info_4",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"\r",
							" var resp_Data = pm.response.json();  //распарсили ответ\r",
							"var req_Data = pm.request.url.query.toObject() //распарсила данные из урла запроса\r",
							"\r",
							"var req_name = req_Data.name //объявила переменную name из запроса\r",
							"pm.test(\"name from request\", function () { //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.name).to.eql(req_name); //сравнила name из ответа  c name  из запроса\r",
							"});\r",
							"\r",
							"var req_age = +req_Data.age //объявила переменную age из запроса\r",
							"pm.test(\"age from request\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.age).to.eql(req_age); //сравнила age из ответа  c age  из запроса\r",
							"});\r",
							"\r",
							"console.log(req_Data.salary) //вывести salary из запроса\r",
							"console.log(resp_Data.salary)//вывести salary  из ответа\r",
							"console.log(resp_Data.salary[0])//вывести 0-й параметр массива salary из ответа\r",
							"console.log(resp_Data.salary[1])//вывести 1-й параметр массива salary из ответа\r",
							"console.log(resp_Data.salary[2])//вывести 2-й параметр массива salary из ответа\r",
							"\r",
							"var req_salary = +req_Data.salary //объявила переменную salary из запроса\r",
							"pm.test(\"salary (param_0) from request\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.salary[0]).to.eql(req_salary); //сравнила 0-й параметр salary из ответа  c salary  из запроса\r",
							"});\r",
							"pm.test(\"salary (param_1) from request\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(+resp_Data.salary[1]).to.eql(req_salary*2); //сравнила 1-й параметр salary из ответа  c salary  из запроса, умноженное на 3\r",
							"});\r",
							"pm.test(\"salary (param_2) from request\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(+resp_Data.salary[2]).to.eql(req_salary*3); //сравнила 2-й параметр salary из ответа  c salary  из запроса, умноженное на 3\r",
							"});\r",
							"\r",
							"\r",
							"var name = req_Data.name //объявляем переменную (значение из запроса)\r",
							"pm.environment.set(\"name\", req_Data.name); // передаем ее в окружение\r",
							"\r",
							"var age = req_Data.age //объявляем переменную  age (значение из запроса)\r",
							"pm.environment.set(\"age\", req_Data.age); // передаем ее в окружение\r",
							"\r",
							"var salary = req_Data.salary //объявляем переменную (значение из запроса)\r",
							"pm.environment.set(\"salary\", req_salary); // передаем ее в окружение\r",
							"\r",
							"for (i = 0; i<resp_Data.salary.length; i++)\r",
							"{console.log(resp_Data.salary[i])};\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{url_1}}/object_info_4?name=Inna&age=30&salary=3000",
					"host": [
						"{{url_1}}"
					],
					"path": [
						"object_info_4"
					],
					"query": [
						{
							"key": "name",
							"value": "Inna"
						},
						{
							"key": "age",
							"value": "30"
						},
						{
							"key": "salary",
							"value": "3000"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "user_info_2",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"\r",
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							" \r",
							" \r",
							"var resp_Data = pm.response.json();  //распарсили данные из  ответа\r",
							"var req_Data = request.data; //распарсила данные из запроса\r",
							"\r",
							"pm.test(\"response has start_qa_salary\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data).to.have.property(\"start_qa_salary\"); // имеется параметр start_qa_salary\r",
							"});\r",
							"pm.test(\"response has qa_salary_after_6_months\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data).to.have.property(\"qa_salary_after_6_months\"); // имеется параметр qa_salary_after_6_months\r",
							"})\r",
							"pm.test(\"response has qa_salary_after_12_months\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data).to.have.property(\"qa_salary_after_12_months\"); // имеется параметр qa_salary_after_12_months\r",
							"})\r",
							"pm.test(\"response has qa_salary_after_1.5_year\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data).to.have.property(\"qa_salary_after_1.5_year\"); // имеется параметр qa_salary_after_1.5_years\r",
							"})\r",
							"pm.test(\"response has qa_salary_after_3.5_years\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data).to.have.property(\"qa_salary_after_3.5_years\"); // имеется параметр qa_salary_after_3.5_years\r",
							"})\r",
							"pm.test(\"person\", function () { //название проверки. Проверить, что...\r",
							"    pm.expect(resp_Data).to.have.property(\"person\"); // имеется параметр person\r",
							"})\r",
							"\r",
							"var req_salary = +req_Data.salary //объявила переменную salary из запроса\r",
							"pm.test(\"start_qa_salary\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.start_qa_salary).to.eql(req_salary); //сравнила start_qa_salary из ответа  c salary  из запроса\r",
							"})\r",
							"pm.test(\"qa_salary_after_6_months\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.qa_salary_after_6_months).to.eql(req_salary*2); //сравнила qa_salary_after_6_months из ответа  c salary*2  из запроса\r",
							"})\r",
							"pm.test(\"qa_salary_after_12_months\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.qa_salary_after_12_months).to.eql(req_salary*2.7); //сравнила qa_salary_after_6_months из ответа  c salary*2.7  из запроса\r",
							"})\r",
							"\r",
							"pm.test(\"qa_salary_after_1.5_year\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data[\"qa_salary_after_1.5_year\"]).to.eql(req_salary*3.3); //сравнила qa_salary_after_1.5_year из ответа  c salary*3.3  из запроса\r",
							"})\r",
							"pm.test(\"qa_salary_after_3.5_years\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data[\"qa_salary_after_3.5_years\"]).to.eql(req_salary*3.8); //сравнила qa_salary_after_3.5_years из ответа  c salary*3.8  из запроса\r",
							"})\r",
							"pm.test(\"u_name\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.person.u_name[1]).to.eql(req_salary); //сравнила 1-й элемент параметра u-name из ответа  c salary  из запроса\r",
							"})\r",
							"var req_age = +req_Data.age //объявила переменную salary из запроса\r",
							"pm.test(\"u_age\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.person.u_age).to.eql(req_age); //сравнила  параметр u-age из ответа  c age  из запроса\r",
							"})\r",
							"pm.test(\"u_salary_5_years\", function () {  //название проверки. Проверить, что...\r",
							"   pm.expect(resp_Data.person.u_salary_5_years).to.eql(req_salary*4.2); //сравнила  параметр u_salary_5_years\" из ответа  c salary*4.2  из запроса\r",
							"})\r",
							"\r",
							"for (key in resp_Data.person) {\r",
							"    console.log(key, resp_Data.person[key]);\r",
							"};\r",
							"\r",
							"\r",
							"\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "formdata",
					"formdata": [
						{
							"key": "name",
							"value": "{{name}}",
							"type": "text"
						},
						{
							"key": "age",
							"value": "{{age}}",
							"type": "text"
						},
						{
							"key": "salary",
							"value": "{{salary}}",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{url_1}}/user_info_2",
					"host": [
						"{{url_1}}"
					],
					"path": [
						"user_info_2"
					]
				}
			},
			"response": []
		}
	]
}
