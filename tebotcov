import telebot
import requests
import time

bot = telebot.TeleBot('1173695328:AAGw9Q342rUxAybLj7a2qwVlqbgrwiq9xYM')

@bot.message_handler(commands=['info'])
def send_covid(message):
    global a 
    global tim
    a = message.from_user.id
    tim = time.time()
    bot.register_next_step_handler(bot.reply_to(message, "Mamlakatni nomini inglizcha kiriting\nMasalan:\nWorld\nUzbekistan\nBelarus\nBelgium\nPortugal\nItaly\nUsa\nChina\nRussia\nKazakhstan\nKyrgyzstan\nSpain\nS. Korea"), check)



def zuxriddin(message):
    bot.register_next_step_handler(message, check)
    
def check(message):
    b = message.from_user.id
    while True:
        

        if a==b:
            send_covid1(message)
            break

        elif tim+15<time.time():
            stop(message)
            break

        else:
            zuxriddin(message)
            break  

def send_covid1(message): 
    
    while True: 
        try:
            url = ('https://coronavirus-19-api.herokuapp.com/countries/{}').format(message.text)
            response = requests.get(url, headers={'Accept':'application/json'})
            data = response.json()
            total = str(data['cases'])
            dead = str(data['deaths'])
            recovered = str(data['recovered'])
            crit = str(data['critical'])
            tod = str(data['todayCases'])
            covid_info = (" {} da : " + "\n" + "Kasallanganlar: " + total + "\n"+"\n" +"Bugun kasallanganlar :"+tod + "\n"+"\n" +"Axvoli jiddiylar :"+crit+ "\n"+"\n" + "vafot etganlar : " + dead + "\n"+"\n"+ "Tuzalganlar: " + recovered+"\n"+"\n"+"Agar yana boshqa Mamlakat haqida ma'lumot olishni istasangiz /info buyrug'ini tanlang").format(message.text)
            bot.reply_to(message, covid_info)
            if covid_info !=None:
                break
        except:
            bot.reply_to(message, "Mamlakat nomi noto'g'ri kiritildi \n /info ni tanlang va qayta urinib ko'ring \n Davlat nomlari Inglizcha yozilishi shart")
            break
def stop(message):
    bot.reply_to(message, "Sizning vahtingiz tugadi agarda ma'lumot kerak bo'lsa /info buyrugini tanlagach 12 soniya ichida davlat nomini kiriting. ") 
bot.polling(none_stop= True) 
