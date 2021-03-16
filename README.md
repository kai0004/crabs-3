# crabs-3
 bot.py
from discord.ext import commands
from discord_slash import SlashCommand

bot = commands.Bot(command_prefix="prefix")
slash = SlashCommand(bot, override_type = True)

bot.load_extension("cog")
bot.run("TOKEN")

# cog.py
import discord
from discord.ext import commands
from discord_slash import cog_ext, SlashContext

class Slash(commands.Cog):
    def __init__(self, bot):
        self.bot = bot

    @cog_ext.cog_slash(name="test")
    async def _test(self, ctx: SlashContext):
        embed = discord.Embed(title="embed test")
        await ctx.send(content="test", embeds=[embed])

def setup(bot):
    bot.add_cog(Slash(bot))
