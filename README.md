# -Міністерство охорони Здоров'я
імпортувати { Картка, Контент Картки } з "@/components/ui/карта";
імпортувати { Кнопку } з "@/components/ui/button";
імпортувати { вхідні дані } з "@/компоненти/ui/input";
імпортувати { Вкладки, TabsList, TabsTrigger, TabsContent } з "@/components/ui/tabs";
імпортувати { Textarea } з "@/components/ui/textarea";
імпорт { Таблиця, Заголовок Таблиці, Рядок Таблиці, Заголовок Таблиці, Тіло Таблиці, Ячейка Таблиці } з "@/components/ui/table";
імпорт {useState } з "реагувати";

експортувати функцію за замовчуванням ClinicHomePage() {
  const [вибранийЛікар, встановитиВибранийЛікар] = useState("");
  константа лікарів = [
    { назва: "Іваненко О.О.", спец: "Терапевт", графік: "Пн, Ср, Пт – 09:00–15:00" },
    { назва: "Петренко Л.С.", спец: "Хірург", графік: "Вт, Пт – 10:00–16:00" },
    { назва: "Сидорчук І.М.", спец: "ЛОР", графік: "Пн, Чт – 11:00–17:00" },
    { назва: "Ковальчук Т.П.", спец: "Педіатр", графік: "Щоденно – 08:00–14:00" },
    { назва: "Гнатюк В.К.", спец: "Офтальмолог", графік: "Вт, Пт – 09:00–13:00" },
    { назва: "Мельник А.Ю.", спец: "Кардіолог", графік: "Ср, Пт – 10:00–16:00" },
    { назва: "Лисенко О.М.", спец: "Дерматолог", графік: "Пн – 09:00–13:00" },
    { назва: "Остапчук І.В.", спец: "Невролог", графік: "Вт, Пт – 12:00–18:00" },
    { назва: "Романюк Н.Л.", спец: "Гінеколог", графік: "Ср, Пт – 08:00–14:00" },
    { назва: "Ткаченко С.О.", спец: "УЗД лікар", графік: "Пн, Ср – 13:00–18:00" },
    { назва: "Демченко І.В.", спец: "Стоматолог", графік: "Щоденно – 10:00–16:00" },
  ];

  const [form, setForm] = useState({ ім'я: '', телефон: '', дата: '', лікар: '' });

  const handleInput = (e) => {
    setForm({ ...форма, [назва_електронної_цілі]: значення_електронної_цілі });
  };

  const handleSubmit = () => {
    alert(`Пацієнт: ${form.name}\nТелефон: ${form.phone}\nЛікар: ${form.doctor}\nДані: ${form.date}\n✅ Запис успішно збережено!`);
  };

  повернення (
    <div className="p-6 space-y-6">
      <h1 className="text-3xl font-bold text-center">Лікарня міста N</h1>
      <p className="text-center">Онлайн-запис до лікаря, інформація для користувачів, контакти</p>

      <Tabs defaultValue="запис">
        <TabsList className="сітка сітка-колони-5">
          <TabsTrigger value="record">Запис до лікаря</TabsTrigger>
          <TabsTrigger value="doctors">Наші лікарі</TabsTrigger>
          <TabsTrigger value="info">Для допомоги</TabsTrigger>
          <TabsTrigger value="services">Операції/Послуги</TabsTrigger>
          <TabsTrigger value="admin">Кабінет</TabsTrigger>
        </TabsList>

        <TabsContent значення="запис">
          <Картка>
            <CardContent className="space-y-4 p-4">
              <h2 className="text-xl font-semibold">Онлайн-запис</h2>
              <Input name="name" placeholder="Ваше ПІБ" onChange={handleInput} />
              <Input name="phone" placeholder="Номер телефону" onChange={handleInput} />
              <select name="doctor" onChange={handleInput} className="w-full border p-2 rounded">
                <option value="">Оберіть лікаря</option>
                {лікарі.map((документ, i) => (
                  <option key={i} value={doc.name}>{doc.name} – {doc.spec}</option>
                ))}
              </select>
              <Input name="date" placeholder="Оберіть дату" type="date" onChange={handleInput} />
              <Button onClick={handleSubmit}>Записатись</Button>
            </CardContent>
          </Card>

          <Card className="mt-6">
            <CardContent className="p-4">
              <h2 className="text-lg font-bold mb-2">Розклад лікарів</h2>
              <Таблиця>
                <Заголовок таблиці>
                  <Рядок таблиці>
                    <TableHead>Прізвище</TableHead>
                    <TableHead>Спеціальність</TableHead>
                    <TableHead>Графік прийому</TableHead>
                  </TableRow>
                </TableHeader>
                <Тіло таблиці>
                  {лікарі.map((документ, i) => (
                    <TableRow key={i}>
                      <TableCell>{назва_документа}TableCell>
                      <TableCell>{doc.spec}TableCell>
                      <TableCell>{doc.schedule}TableCell>
                    </TableRow>
                  ))}
                </TableBody>
              </Table>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="лікарі">
          <div className="сітка сітка-колони-2 проміжок-4">
            {лікарі.map((документ, i) => (
              <Ключ картки={i}>
                <CardContent className="p-4 space-y-2">
                  <h3 className="font-bold text-lg">{назва_документа}
                  <p>{doc.spec}
                  <p><strong>Графік:</strong> {doc.schedule}</p>
                </CardContent>
              </Card>
            ))}
          </div>
        </TabsContent>

        <TabsContent значення="інформація">
          <Картка>
            <CardContent className="space-y-3 p-4">
              <h2 className="text-xl font-bold">Інформація для сім'ї</h2>
              <p>🔹 Як підготуватися до прийому</p>
              <p>🔹 Які документи брати</p>
              <p>🔹 Що робити при екстреній ситуації</p>
              <p>🔹 Як скасувати запис</p>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent значення="послуги">
          <Картка>
            <CardContent className="p-4 space-y-2">
              <h2 className="text-xl font-bold">Виді операції та послуги</h2>
              <ul className="список-дисків pl-4">
                <li>Операції: апендицит, грижі, жовчний міхур</li>
                <li>Стоматологія: лікування, видалення, протезування</li>
                <li>УЗД, рентген, ЕКГ</li>
                <li>Вакцинація дітей та дорослих</li>
              </ul>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent значення="адміністратор">
          <Картка>
            <CardContent className="p-4 space-y-3">
              <h2 className="text-xl font-semibold">Кабінет працівника</h2>
              <Input placeholder="Логін" />
              <Input placeholder="Пароль" type="password" />
              <Button>Увійти</Button>
            </CardContent>
          </Card>
        </TabsContent>
      </Tabs>
    </div>
  );
}-
