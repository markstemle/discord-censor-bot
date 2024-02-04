import discord
from discord import Intents

# List of bad words to censor
BAD_WORDS = ["badword", "dirtyword", "rudeword"] 

intents = Intents.default()
intents.messages = True
intents.message_content = True
intents.guilds = True
intents.guild_messages = True

client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'We have logged in as {client.user}')

@client.event
async def on_message(message):

    if message.author == client.user:
        return

    original_message_content = message.content
    message_content_lower = original_message_content.lower()

    bad_word_found = False

    for bad_word in BAD_WORDS:
        if bad_word in message_content_lower:
            # Replace the bad word with asterisks in the original message
            censored_word = '*' * len(bad_word)
            original_message_content = original_message_content.replace(bad_word, censored_word)
            bad_word_found = True

    if bad_word_found:
        await message.delete()
        await message.channel.send(f"{message.author.mention} said: {original_message_content}")

TOKEN = <discord token> 
client.run(TOKEN)
