from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, filters, ContextTypes

import os

TOKEN = os.getenv("TOKEN")

FAQ_ANSWERS = {
    "start": "Welcome to the B&S SAT and Admission Program! Type your question or ask for help.",
    "when does the course start": "The course starts on July 18th and runs for 2 months.",
    "is it online": "Yes! The course is 100% online.",
    "how do I register": "You can register through our online form. (Link coming soon!)",
    "what’s included in the course": "3 SAT English + 3 SAT Math lessons + up to 2 admissions sessions weekly.",
    "who are the teachers": "Our teachers have 1+ year experience. Admission mentors study at top 10 U.S. universities.",
    "is there a discount": "We offer 3 plans: Full $95, Partial $65, Admission Only $49.",
    "what level of english": "IELTS 6 or equivalent level is enough. You just need basic math & English to join."
}

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text(FAQ_ANSWERS["start"])

async def reply_to_question(update: Update, context: ContextTypes.DEFAULT_TYPE):
    text = update.message.text.lower()
    for key in FAQ_ANSWERS:
        if key in text:
            await update.message.reply_text(FAQ_ANSWERS[key])
            return
    await update.message.reply_text("Thanks for your message! A team member will reply to you soon.")

app = ApplicationBuilder().token(TOKEN).build()

app.add_handler(CommandHandler("start", start))
app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, reply_to_question))

app.run_polling()
