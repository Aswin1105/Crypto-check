# Crypto-check


Hi I am Aswin.B

The task completed are 
Create a rest API endpoint for the user’s to create an alert `alerts/create/`
- Create a rest API endpoint for the user’s to delete an alert `alerts/delete/`
- Create a rest API endpoint to fetch all the alerts that the user has created.
Also done the crypto checking to some extend with the already defined curr_price
the tools used in this project may not be what Krypto expected but due to time contraint i used my comfort tools
This incomplete project submission is only due to my acadamics examinations
Sorry for inconvinence

### Project explanation:

The project has two parts namely anvil (for frontend) and Colab (For backend). Both are python based.
# Frontend
Anvil creates a server client model to prepare a end to end to connection for data retrival.
This is the webapp link : https://664ZH2Q3JW3DUKJA.anvil.app/C6EJWGRFQQIBSNOXIAMGAFVE
The building models and code will be available as photos.

# Backend 
In backend i used python to store the data in colab until the session expires or user is online.
The colab notebook has to run and kept active (server should be kept active), for the anvil to work
$$$$ IMPORTANT NOTE: THE COLAB ANVIL FOREVER CODE BLOCK WILL BE RUNNING FOREVER PLS STOP IT, EVEN THEN THE SERVER WILL BE ACTIVE UNTIL COLAB SESSION EXPIRES 
the link for colab: https://colab.research.google.com/drive/1hw67qTNgp4h5fwp8_U7NvFvA0lz9j-Fp?usp=sharing

# steps to run

Run the server colab code before running the app or pressing enter in the app
if the server is active then anvil can CREATE, DELETE AND FETCH ALL DATA PERFECTLY
first feed some data to storage (create some triggers)
then we can use fetch and delete

# incomplete part
till now i was only able to cmpare already stored value rather than updating value through web scraping (Beautiful soup or selenium)
the comparison of the data only happens when you create a data trigger, this may be made into a iterative process

### ANVIL CODE
from ._anvil_designer import Form1Template
from anvil import *
import anvil.server

class Form1(Form1Template):

  def __init__(self, **properties):
    # Set Form properties and Data Bindings.
    self.init_components(**properties)

    # Any code you write here will run when the form opens.
      

  def button_1_click(self, **event_args):
    pheal = ""
    if (self.drop_down_1.selected_value ==self.drop_down_1.items[0] or self.drop_down_2.visible != True):
      self.drop_down_2.visible = True
      self.text_box_1.visible =True
      self.text_box_2.visible =True
      self.button_1.visible = False
      self.button_2.visible = True
    pass

  def button_2_click(self, **event_args):
    if(self.drop_down_2.visible == True):
      if self.drop_down_2.selected_value ==self.drop_down_2.items[0]:
        pheal = anvil.server.call('Create',self.text_box_1.text,self.text_box_2.text)
      elif self.drop_down_2.selected_value =="Delete":
        pheal = anvil.server.call('Delete',self.text_box_1.text,self.text_box_2.text)
      elif self.drop_down_2.selected_value =="Fetch":
        p1 = anvil.server.call('Fetch')
        pheal = str(p1)
    self.text_area_1.visible = True
    self.text_area_1.text = "".join(pheal)
    pass



