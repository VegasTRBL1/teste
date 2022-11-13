import discord
from discord import app_commands

id_do_servidor =  1025516683160461373

class client(discord.Client):
    def __init__(self):
        super().__init__(intents=discord.Intents.default())
        self.synced = False 

    async def on_ready(self):
        await self.wait_until_ready()
        if not self.synced: 
            await tree.sync(guild = discord.Object(id=id_do_servidor)) 
            self.synced = True
        print(f"Entramos como {self.user}.")

aclient = client()
tree = app_commands.CommandTree(aclient)

@tree.command(guild = discord.Object(id=id_do_servidor), name = 'teste', description='Testando') 
async def slash2(interaction: discord.Interaction):
    await interaction.response.send_message(f"Estou funcionando!", ephemeral = True) 

aclient.run('OTcyODg1MTg5MTI4Nzc3ODQ5.GrUpzi.LjQNkuFpTJsbNYXH6s5RdKc55oHm5J0CJHMHJc')
