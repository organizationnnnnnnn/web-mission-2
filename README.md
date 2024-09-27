# Mission 3

## Part 0

[(https://oa1x4y.buildship.run/task4)](https://drive.google.com/file/d/1feBLBhLcAuk2CHnC7CCcyk1eszn-b65m/view?usp=sharing)

## Part3

- получить список юзернеймов пользователей
  ```sql
  select username from users;
  ```

- получить кол-во отправленных сообщений каждым пользователем: username - number of sent messages 
``` sql
select users.username, count(messages.id) as number_of_sent_messages from users left join messages on users.id = messages.id group by users.username;
```

- Получить пользователя с самым большим кол-вом полученных сообщений и само количество: username - number of received messages 
``` sql
select users.username, count(messages.id) as number_of_received_messages from users left join messages on users.id = messages.to group by users.username order by number_of_received_messages desc limit 1;
```

- Получить среднее кол-во сообщений, отправленное каждым пользователем
``` sql select avg(sent_count) as average_sent_messages from (select count(messages.id) as sent_count from users  left join messages on users.id = messages.from group by users.id) as subquery;
```
