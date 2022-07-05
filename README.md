HW_2 Postman

1) http://162.55.220.72:5005/first
  1. Отправить запрос.
  2.  // Статус код 200
                pm.test("Status code is 200", function () {
                    pm.response.to.have.status(200);
                });

  3.  // Проверить, что в body приходит правильный string.
                pm.test("Body is correct", function () {
                    pm.response.to.have.body("This is the first responce from server!ss");
                });
      
2) http://162.55.220.72:5005/user_info_3
  1. Отправить запрос.
  
                //2. Статус код 200
                pm.test("Status code is 200", function () {
                    pm.response.to.have.status(200);
                });

                 //3. Спарсить response body в json.
                 let jsonData = pm.response.json();  

                // 4. Проверить, что name в ответе равно name s request (name вбить руками.)
                pm.test("Check_name", function () {
                  pm.expect(jsonData.name).to.eql("Ildana");
                });

                // 5. Проверить, что age в ответе равно age s request (age вбить руками.)
                pm.test("Check_age", function () {
                  pm.expect(jsonData.age).to.eql("39");
                });

                // 6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
                pm.test("Check_salary", function () {
                  pm.expect(jsonData.salary).to.eql(2000);
                });

                // 7. Спарсить request.
                let req = request.data;

                // 8. Проверить, что name в ответе равно name s request (name забрать из request.)
                let name_s = req.name;
                //console.log(name_s);
                pm.test("Check_name2", function () {
                  pm.expect(jsonData.name).to.eql(name_s);
                });

                // 9. Проверить, что age в ответе равно age s request (age забрать из request.)
                let age_s = req.age;
                //console.log(age_s);
                pm.test("Check_age2", function () {
                  pm.expect(jsonData.age).to.eql(age_s);
                });

                //10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)

                let salary_s = req.salary;
                //console.log(salary_s);
                pm.test("Check_salary2", function () {
                    pm.expect(jsonData.salary).to.eql(+(salary_s));
                  //pm.expect(jsonData.salary).to.eql(salary_s); 
                });

                //11. Вывести в консоль параметр family из response.

                console.log(jsonData.family);

                //12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)

                let u_salary_1_5_year = jsonData.family.u_salary_1_5_year;
                //console.log(u_salary_1_5_year);
                let salary_r = req.salary;
                //console.log(salary_r);

                pm.test("u_salary_1_5_year", function () {
                  pm.expect(u_salary_1_5_year).to.eql(+(salary_r*4));
                });
                
 3) http://162.55.220.72:5005/object_info_3
    1. Отправить запрос.
  
              //2. Статус код 200
              pm.test("Status code is 200", function () {
                  pm.response.to.have.status(200);
              });

              //3. Спарсить response body в json.
              let resBody = JSON.parse(responseBody) // to parse json response

              // 4. Спарсить request.
              let reqBody = pm.request.url.query.toObject() //  to parse json request

              //5. Проверить, что name в ответе равно name s request (name забрать из request.)
              let name_s = reqBody.name;
              pm.test("Check_name", function () {
                pm.expect(resBody.name).to.eql(name_s);
              });

              // 6. Проверить, что age в ответе равно age s request (age забрать из request.)

              let age_s = reqBody.age;
              pm.test("Check_age", function () {
                pm.expect(resBody.age).to.eql(age_s);
              });

              // 7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)

              let salary_s = reqBody.salary;
              pm.test("Check_salary", function () {
                pm.expect(resBody.salary).to.eql(+salary_s);
              });

              // 8. Вывести в консоль параметр family из response.
              console.log(resBody.family);

              // 9. Проверить, что у параметра dog есть параметры name.
              pm.test("Dog has parametr name", function() {
                pm.expect(resBody).to.have.property("name");
              });

              // 10. Проверить, что у параметра dog есть параметры age.
              pm.test("Dog has parametr age", function() {
                pm.expect(resBody).to.have.property("age");
              });

              // 11. Проверить, что параметр name имеет значение Luky.
              let param_name = resBody.family.pets.dog.name
              pm.test("Parametr name Luky", function() {
                pm.expect(param_name).to.eql("Luky");
              });

              // 12. Проверить, что параметр age имеет значение 4.
              let param_age = resBody.family.pets.dog.age
              pm.test("Parametr age 4", function() {
                pm.expect(param_age).to.eql(4);
              });

4) http://162.55.220.72:5005/object_info_4
    1. Отправить запрос.
  
        //2. Статус код 200
        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });

        //3. Спарсить response body в json.
         let resbody = pm.response.json();   // to parse json response

         //4. Спарсить request.
        let reqBody = pm.request.url.query.toObject() //  to parse json request

        //5. Проверить, что name в ответе равно name s request (name забрать из request.)
        let name_req = reqBody.name
        pm.test("Check name response", function () { 
            pm.expect(resbody.name).to.eql(name_req);
        });

        //6. Проверить, что age в ответе равно age из request (age забрать из request.)
        let age_req = reqBody.age
        pm.test("Check age response", function () { 
            pm.expect(resbody.age).to.eql(+age_req);
        });

        //7. Вывести в консоль параметр salary из request
        let salary_req = reqBody.salary
        //console.log(salary_req);

        //8. Вывести в консоль параметр salary из response
        let salary_res = resbody.salary
        //console.log(salary_res);

        //9. Вывести в консоль 0-й элемент параметра salary из response.
        //console.log(salary_res[0]);

        //10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
        //console.log(salary_res[1]);

        //11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
        //console.log(salary_res[2]);

        //12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
        pm.test("Check salary[0]", function () { 
            pm.expect(salary_res[0]).to.eql(+salary_req);
        });

        //13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
        pm.test("Check salary[1]", function () { 
            pm.expect(+salary_res[1]).to.eql(salary_req*2);
        });

        //14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
        pm.test("Check salary[2]", function () { 
            pm.expect(+salary_res[2]).to.eql(salary_req*3);
        });

        // 18. Передать в окружение переменную name       
             pm.environment.set("name",name_req);

        // 19. Передать в окружение переменную age   
             pm.environment.set("age",age_req); 

        // 20. Передать в окружение переменную salary  
             pm.environment.set("salary",salary_req); 

        //21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
        let salary = resbody.salary;
        for (let i=0; i<salary.length; i+=1){
        console.log(salary[i])}

5) http://162.55.220.72:5005/user_info_2
    1. Вставить параметр salary из окружения в request
    2. Вставить параметр age из окружения в age
    3. Вставить параметр name из окружения в name
    4. Отправить запрос.
   
        // 5. Статус код 200
        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });

        //6. Спарсить response body в json
        let resbody = pm.response.json();

        //7. Спарсить request.
        let reqbody = request.data;

        //8. Проверить, что json response имеет параметр start_qa_salary
        pm.test("response has parametr start_qa_salary", function () {
            pm.expect(resbody).to.have.property("start_qa_salary");
        });

        //9. Проверить, что json response имеет параметр qa_salary_after_6_months
        pm.test("response has parametr qa_salary_after_6_months", function () {
            pm.expect(resbody).to.have.property("qa_salary_after_6_months");
        });

        //10. Проверить, что json response имеет параметр qa_salary_after_12_months
        pm.test("response has parametr qa_salary_after_12_months", function () {
            pm.expect(resbody).to.have.property("qa_salary_after_12_months");
        });

        //11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
        pm.test("response has parametr qa_salary_after_1.5_year", function () {
            pm.expect(resbody).to.have.property("qa_salary_after_1.5_year");
        });

        //12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
        pm.test("response has parametr qa_salary_after_3.5_years", function () {
            pm.expect(resbody).to.have.property("qa_salary_after_3.5_years");
        });

        //13. Проверить, что json response имеет параметр person
        pm.test("response has person", function () {
            pm.expect(resbody).to.have.property("person");
        });

        //14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
        let salary_req = +reqbody.salary
        pm.test("Check_start_qa_salary", function () {
            pm.expect(resbody.start_qa_salary).to.eql(salary_req);
        });

        //15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
        let salary_req2 = reqbody.salary * 2
        pm.test("Check_qa_salary_after_6_months", function () {
            pm.expect(resbody.qa_salary_after_6_months).to.eql(salary_req2);
        });

        //16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
        let salary_req3 = reqbody.salary * 2.7
        pm.test("qa_salary_after_12_months", function () {
            pm.expect(resbody.qa_salary_after_12_months).to.eql(salary_req3);
        });

        //17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
        let salary_req4 = reqbody.salary * 3.3
        pm.test("qa_salary_after_1.5_year", function () {
            pm.expect(resbody["qa_salary_after_1.5_year"]).to.eql(salary_req4);
        });

        //18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
        let salary_req5 = reqbody.salary * 3.8
        pm.test("qa_salary_after_3.5_years", function () {
            pm.expect(resbody["qa_salary_after_3.5_years"]).to.eql(salary_req5);
        });

        //19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
        let salary_req6 = +reqbody.salary
        let person_salary = resbody.person.u_name[1];

        pm.test("Check_person_salary", function () {
            pm.expect(person_salary).to.eql(salary_req6);
        });

        //20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
        let age_req = +reqbody.age
        let u_age = resbody.person.u_age

        pm.test("Check u_age", function () {
            pm.expect(u_age).to.eql(age_req);
        });

        //21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
        let salary_req7 = +reqbody.salary * 4.2
        let u_salary_5_years = resbody.person.u_salary_5_years

        pm.test("Check u_salary_5_years", function () {
            pm.expect(u_salary_5_years).to.eql(salary_req7);
        });

        //22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
        let person2 = resbody.person;
        let keys= Object.keys(person2) //преобразуем ключи объекта в массив

        for (let i=0; i<keys.length; i+=1){
        console.log(keys[i],person2[keys[i]])
        }
