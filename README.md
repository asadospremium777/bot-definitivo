import discord
import os
import random
from discord.ext import commands
import requests
from bot_logic import gen_pass
from bot_logic import get_duck_image_url

# La variable intents almacena los privilegios del bot
intents = discord.Intents.default()
# Activar el privilegio de lectura de mensajes
intents.message_content = True
# Crear un bot en la variable cliente y transferirle los privilegios
bot = commands.Bot(command_prefix = '$', intents = intents)

@bot.event
async def on_ready():
    print(f'hemos iniciado secion como {bot.user}')

@bot.command()
async def bye(ctx):
        await ctx.send('hy')

@bot.command()
async def problemas(ctx):
        await ctx.send('😓')

@bot.command()
async def contraseña(ctx):
        await ctx.send(gen_pass(10))

@bot.command()
async def jesus(ctx):
    await ctx.send('yo confio en tí.')

@bot.command()
async def mem(ctx):
    with open('images/mem1.jpg', 'rb') as f:
        # ¡Vamos a almacenar el archivo de la biblioteca Discord convertido en esta variable!
        picture = discord.File(f)
    # A continuación, podemos enviar este archivo como parámetro.
    await ctx.send(file=picture)

@bot.command()
async def mem(ctx):
    mem_alet = random.choice(os.listdir("images"))
    with open(f'images/{mem_alet}', 'rb') as f:
        # ¡Vamos a almacenar el archivo de la biblioteca Discord convertido en esta variable!
        picture = discord.File(f)
    # A continuación, podemos enviar este archivo como parámetro.
    await ctx.send(file=picture)



@bot.command('duck')
async def duck(ctx):
    '''Una vez que llamamos al comando duck, 
    el programa llama a la función get_duck_image_url'''
    image_url = get_duck_image_url()
    await ctx.send(image_url)

@bot.command()
async def mem(ctx):
    mem_alet = random.choice(os.listdir("images"))
    with open(f'images/{mem_alet}', 'rb') as f:
        # ¡Vamos a almacenar el archivo de la biblioteca Discord convertido en esta variable!
        picture = discord.File(f)
    # A continuación, podemos enviar este archivo como parámetro.
    await ctx.send(file=picture)





bot.run("MTI3ODE1NzQzOTM0MTk1NzIzNA.GItElN.Gg4d1Waf8l2Dm1ldGk1f8tKEGcFt9GR5jwhA90")
