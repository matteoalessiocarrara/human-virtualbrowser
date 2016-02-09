# Human Virtualbrowser #

Browser headless scritto in python, ispirato ai browser con gui

Questa libreria contiene un oggetto browser utilizzabile in python, molto simile
ai comuni browser come firefox. Per questo, dovrebbe essere molto semplice e intuitivo.
Purtroppo però, il fatto di essere ispirato a browser con gui e non avere una gui
lo rende scomodo per un utilizzo reale. Quindi ho scritto un wrapper ottimizzato
per i bot, lo trovate [qui](https://github.com/matteoalessiocarrara/bot-virtualbrowser).

## Esempio ##

```python
import virtualbrowser
import logging
import version


logging.basicConfig(level=logging.WARNING)

# Apriamo il browser
browser = virtualbrowser.Browser()

# Aprendo il browser, si apre anche una finestra
window = browser.windows_manager.windows.values()[0]

# Ogni finestra contiene almeno una scheda
tab = window.tabs_manager.tabs.values()[0]

# Scriviamo l'url nella barra degli indirizzi
tab.url = "https://www.python.org/"

# Premiamo invio, e carichiamo la pagina
tab.download_content()

print "Il titolo della pagina nella scheda 1 è", tab.bs_content.title.text

# Ora vogliamo aprire una nuova scheda
tab2 = window.tabs_manager.add_tab("https://google.com")

# Ccarichiamo la pagina
tab2.download_content()

print "Il titolo della pagina nella scheda 2 è", tab2.bs_content.title.text

# Torniamo sulla scheda 1, è sempre aperta
print "Il titolo della pagina nella scheda 1 è", tab.bs_content.title.text

# Ora apriamo una nuova finestra
window2 = browser.windows_manager.add_window()

# Anche in questa, c'è già una scheda aperta
tab3 =  window2.tabs_manager.tabs.values()[0]

tab3.url = "https://m.facebook.com"
tab3.download_content()

# Dimostriamo che ci sono sempre tre schede aperte
print "Il titolo della pagina nella scheda 3 è", tab3.bs_content.title.text
print "Il titolo della pagina nella scheda 2 è", tab2.bs_content.title.text
print "Il titolo della pagina nella scheda 1 è", tab.bs_content.title.text

# Ora usciamo
window2.close()
window.close()
```

## Requisiti ##

 * Python 2
 * [BeautifulSoup 4](http://www.crummy.com/software/BeautifulSoup/#Download)
 * [Requests](http://docs.python-requests.org/en/master/user/install/#install)

## Codice ##

La sintassi delle docstring è ispirata a quella usata da [NumPy](https://github.com/numpy/numpy/)


## Altre informazioni ##

> This is the Unix philosophy: Write programs that do one thing and do it well.
  Write programs to work together. Write programs to handle text streams, because
  that is a universal interface.

Aggiornamenti: [GitHub](https://github.com/matteoalessiocarrara/human-virtualbrowser)  
Email: sw.matteoac@gmail.com
