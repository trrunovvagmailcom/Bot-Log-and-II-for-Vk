import vk_api, json, requests, apiai
from vk_api.bot_longpoll import VkBotLongPoll, VkBotEventType
from vk_api.longpoll import VkLongPoll, VkEventType
from vk_api.utils import get_random_id
import datetime



###
### Авторизация бота в группе
###

vk_session = vk_api.VkApi(token='4d56e093b9fffd71cf9a5344a89e720ea2b247630b005bcdda933508b1c3a72ccec9c9a81a34670b99c5e')
vk = vk_session.get_api()
longpoll = VkBotLongPoll(vk_session, '32683970')
longpollS = VkLongPoll(vk_session)
session = requests.Session()

###
### Клавиатура бота
###


def get_button(label, color, payload=""):
   return {
           "action": {
           "type": "text",
           "payload": json.dumps(payload),
           "label": label
           },
           "color": color
           }
keyboard = {
   "one_time": False,
   "buttons": [
       [get_button(label="Хочу поехать на стажировку", color="positive")],
       [get_button(label="О стажировках", color="negative", payload="{\"button\": \"1\"}"),
        get_button(label="Наши проекты", color="primary", payload="{\"button\": \"2\"}")],
       [get_button(label="Ближайшие мероприятия", color="positive")]
   ]}
keyboard = json.dumps(keyboard, ensure_ascii=False).encode('utf-8')
keyboard = str(keyboard.decode('utf-8'))
keyboardOppo = {
   "one_time": True,
   "buttons": [
       [get_button(label="Global Volunteer", color="negative")],
       [get_button(label="Global Entrepreneur", color="primary", payload="{\"button\": \"2\"}")],
       [get_button(label="Global Talent", color="positive")],
       [get_button(label="Вернуться в меню", color="default")]
   ]}
keyboardOppo = json.dumps(keyboardOppo, ensure_ascii=False).encode('utf-8')
keyboardOppo = str(keyboardOppo.decode('utf-8'))
keyboardBotOpen = {
   "one_time": False,
   "buttons": [
       [get_button(label="Выйти из диалога", color="positive")]
   ]}
keyboardBotOpen = json.dumps(keyboardBotOpen, ensure_ascii=False).encode('utf-8')
keyboardBotOpen = str(keyboardBotOpen.decode('utf-8'))
keyboardProject = {
   "one_time": False,
   "buttons": [
       [get_button(label="Форумы", color="negative")],
       [get_button(label="Английский клуб", color="primary")],
       [get_button(label="Ближайшие события", color="default")],
       [get_button(label="Проекты с иностранцами", color="positive")]
   ]}
keyboardProject = json.dumps(keyboardProject, ensure_ascii=False).encode('utf-8')
keyboardProject = str(keyboardProject.decode('utf-8'))
keyboardProjectForeigner = {
   "one_time": False,
   "buttons": [
       [get_button(label="Buddy", color="negative",  payload="{\"button\": \"1\"}"),
       get_button(label="Host-family", color="primary",  payload="{\"button\": \"2\"}")],
       [get_button(label="Вернуться в меню", color="positive")]
   ]}
keyboardProjectForeigner = json.dumps(keyboardProjectForeigner, ensure_ascii=False).encode('utf-8')
keyboardProjectForeigner = str(keyboardProjectForeigner.decode('utf-8'))


def mainlog():
   print("Рабочий вариант бота тут", '\n')
   for event in longpoll.listen():
       ### Дата события
       today = datetime.datetime.today()
       dataForSite = today.strftime('%Y-%m-%d')
       if event.type == VkBotEventType.MESSAGE_NEW:###ЕСЛИ ПОСТУПИЛО НОВОЕ СООБЩЕНИЕ
           Message_New = open('D:\Projects\MassMessages.txt', 'a')
           print('Входящее сообщение:', today.strftime(" %H:%M %d.%m.%Y"), '\n',###ЗАПИСАТЬ В ФАЙЛ
                 'От: https://vk.com/id', event.obj.from_id, '\n', 'Текст: ',
                 event.obj.text, sep='', end='\n\n', file=Message_New)
           Message_New.close()
           print('Входящее сообщение:', today.strftime(" %H:%M %d.%m.%Y"), '\n',###НА ЭКРАН
                 'От: https://vk.com/id', event.obj.from_id, '\n', 'Текст: ',
                 event.obj.text, sep='', end='\n\n')

           request = event.object.text
           if request == "Начать":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(), message='Привет')
           elif request == "начать":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(), message='Привет')
           elif request == "Start":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(), message='Привет')
           elif request == "start":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(), message='Привет')
           elif request == "Старт":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(), message='Привет')
           elif request == "старт":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(), message='Привет')

           elif request == "Хочу поехать на стажировку":
               vk.messages.send(user_id=event.obj.from_id,
               random_id=get_random_id(), keyboard=keyboardOppo, message="Оставляй заявку и с тобой свяжутся в течение 24 часов. Переходи: https://vk.com/aiesec_vrn?w=app5708398_-15485470")

           elif request == "Наши проекты":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), keyboard=keyboardProject, message='Мы разрабатываем и организуем следующие проекты, нажми что бы узнать больше')
           elif request == "Форумы":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), message='AIESEC - организатор ежегодных форумов YouLead и BreakPoint\n\n'
                                                                                              'Форум молодых лидеров YouLead\n'
                                                                                              'Это платформа для социального и профессионального развития личности посредством обмена мыслями, опытом и возможностью реализации.\n'
                                                                                              'https://vk.com/youlead_vrn\n\n'
                                                                                              'Форум для студентов технических специальностей Breakpoint\n'
                                                                                              'Это площадка для самоопределения, взаимодействия с единомышленниками, а также место для обмена опытом и общения с интересными людьми.\n'
                                                                                              'https://vk.com/breakpointvrn\n\n')
           elif request == "Английский клуб":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), message='Проект “Speaking Club”- увлекательная возможность бесплатно развивать разговорный навык на практике! Не упусти свой шанс, присоединяйся!\n'
                                                                                              'https://vk.com/speak_eng_aiesec_vrn\n'
                                                                                              'https://vk.com/event180944048')
           elif request == "Ближайшие события":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), message='Узнать подробнее о культуре принимающей страны и ознакомиться с подробностями наших проектов ты сможешь на инфосессиях.\n'
                                                                                              'Будь в курсе мероприятий, вступай во встречи:\n'
                                                                                              'https://vk.com/event181196348\n'
                                                                                              'https://vk.com/event180944048')
           elif request == "Проекты с иностранцами":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), keyboard=keyboardProjectForeigner, message='Хотим познакомить Вас с новой программой в рамках летнего проекта Sunshine - «Host and buddy»\nЧто такое host и buddy?\n')
           elif request == "Host-family":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), message='Host - это гостевая семья или люди (студенты, работники и др.), принимающие у себя иностранного стажёра в период его нахождения на стажировке.\nВступай в группу и заполняй анкету: https://vk.com/host_me_vrn\n\n')
           elif request == "Buddy":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), message='Buddy - это друг из России, который периодически (или даже пару раз) проводит время со стажёром, на момент его пребывания на стажировке.\nГуляет с ним, показывает ему город, обменивается с ним опытом и знанием языка.\nПонятия host и buddy схожи. Когда Вы являетесь host, то Вы не только предоставляете иностранному стажёру жилье, но и общаетесь с ним, обмениваетесь опытом и знанием языка, весело проводите время\n Вступай в группу и заполняй анкету: https://vk.com/host_me_vrn')


           elif request == "О стажировках":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboardOppo, random_id=get_random_id(), message='Узнай больше о наших проектах')
           elif request == "Global Volunteer":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboardOppo, random_id=get_random_id(),
                                message='Global Volunteer\n'
                                        '6-8 недель работы над волонтерским проектом в международной команде и в абсолютно новой культуре.'
                                        'Каждый проект направлен на достижение одной из Целей Устойчивого Развития ООН.\n'
                                        'Подробнее: https://aiesec.ru/global-volunteer/\n'
                                        'Регистрируйся на сайте: https://auth.aiesec.org/users/sign_in#signup\n\n')
               #vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(),
                               # message='&#13;')
                                        #'Актуальные стажировки\n https://aiesec.org/search?type=1&earliest_start_date=' + dataForSite + '&sort=relevance')
           elif request == "Global Entrepreneur":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboardOppo, random_id=get_random_id(),
                                message='Global Entrepreneur\n'
                                        '1,5 — 3 месяца опыта на стажировке в малом бизнесе или стартапе в продажах,'
                                        'маркетинге или IT в абсолютно новой культуре.\n'
                                        'Подробнее: https://aiesec.ru/global-entrepreneur/\n'
                                        'Регистрируйся на сайте: https://auth.aiesec.org/users/sign_in#signup\n\n')
              # vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(),
                                #message='&#13;')
                                       # 'Актуальные стажировки\n https://aiesec.org/search?type=5&earliest_start_date=' + dataForSite + '&sort=relevance')
           elif request == "Global Talent":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboardOppo, random_id=get_random_id(),
                                message='Global Talent\n'
                                        '3-12 месяцев на практической стажировке по направлениям: маркетинг, продажи, IT, '
                                        'инжиниринг, преподавание, отельный менеджмент, бизнес администрирование в абсолютно новой культуре.\n'
                                        'Подробнее: https://aiesec.ru/global-talent/\n'
                                        'Регистрируйся на сайте: https://auth.aiesec.org/users/sign_in#signup\n\n')
                                        #'Выбрать направление стажировки:')
               #vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(),
                                #message='&#13;')
                                        #'Актуальные стажировки\n https://aiesec.org/search?type=2&earliest_start_date=' + dataForSite + '&sort=relevance')

           elif request == "Вернуться в меню":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), keyboard=keyboard, message='Начальное меню')

           elif request == "Ближайшие мероприятия":
               vk.messages.send(user_id=event.obj.from_id, random_id=get_random_id(), message='Узнать подробнее о культуре принимающей страны и ознакомиться с подробностями наших проектов ты сможешь на инфосессиях.\n'
                                                                                              'Будь в курсе мероприятий, вступай во встречи:\n'
                                                                                              'https://vk.com/event181196348\n'
                                                                                              'https://vk.com/event180944048')

           elif request == "Диалог с Ботом":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboardBotOpen, random_id=get_random_id(), message='Сейчас,мы его разбудим')
               for event in longpollS.listen():
                   if event.type == VkEventType.MESSAGE_NEW and event.to_me and event.text:
                       request1 = event.text
                       print(request, '\n')
                       request = apiai.ApiAI(
                           '246b102d97034fd2974a4ddddd767081').text_request()  # Токен API к Dialogflow
                       request.lang = 'en'
                       request.session_id = 'BatlabAIBot'  # ID Сессии диалога (нужно, чтобы потом учить бота)
                       request.query = event.text  # Посылаем запрос к ИИ с сообщением от юзера
                       responseJson = json.loads(request.getresponse().read().decode('utf-8'))
                       response = responseJson['result']['fulfillment']['speech']  # Разбираем JSON и вытаскиваем ответ
                       print(request, '\n')
                       # Если есть ответ от бота - присылаем юзеру, если нет - бот его не понял
                       if response:
                           vk.messages.send(user_id=event.user_id, random_id=get_random_id(), message=response)
                       elif request1 == "Выйти из диалога":
                           vk.messages.send(user_id=event.user_id, keyboard=keyboard, random_id=get_random_id(),
                                            message='Good Luck!')
                           break
           elif request == "Выйти из диалога":
               vk.messages.send(user_id=event.obj.from_id, keyboard=keyboard, random_id=get_random_id(),
                                message='Good Luck!')
               break

       elif event.type == VkBotEventType.MESSAGE_REPLY:
           Message_Reply = open('D:\Projects\MassMessages.txt', 'a')
           print('Исходящее сообщение: ', today.strftime("%H:%M %d.%m.%Y"), '\n',
                 'Для: https://vk.com/id', event.obj.peer_id, '\n', 'Текст: ',
                 event.obj.text, sep='', end='\n\n', file=Message_Reply)
           Message_Reply.close()
           print('Исходящее сообщение: ', today.strftime("%H:%M %d.%m.%Y"), '\n',
                 'Для: https://vk.com/id', event.obj.peer_id, '\n', 'Текст: ',
                 event.obj.text, sep='', end='\n\n')

       elif event.type == VkBotEventType.GROUP_JOIN:
           Join = open('D:\Projects\ListPerson_JOIN.txt', 'a')
           print('Вступил в группу: ', today.strftime("%H:%M %d.%m.%Y"), '\n',
                 'https://vk.com/id', event.object.user_id, sep='', end='\n\n', file=Join)
           Join.close()
           print('Вступил в группу: ', today.strftime("%H:%M %d.%m.%Y"), '\n',
                 'https://vk.com/id', event.object.user_id, sep='', end='\n\n')

       elif event.type == VkBotEventType.GROUP_LEAVE:
           Leave = open('D:\Projects\ListPerson_LEAVE.txt', 'a')
           print('Покинул группу: ', today.strftime("%H:%M %d.%m.%Y"), '\n',
                 'https://vk.com/id', event.obj.user_id, sep='', end='\n\n', file=Leave)
           Leave.close()
           print('Покинул группу: ', today.strftime("%H:%M %d.%m.%Y"), '\n',
                 'https://vk.com/id', event.obj.user_id, sep='', end='\n\n')

if __name__ == '__main__':
   mainlog()


