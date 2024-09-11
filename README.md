# signals.py
import time
from django.dispatch import Signal, receiver

# Define a custom signal
my_signal = Signal()

# Receiver function with a deliberate delay
@receiver(my_signal)
def my_receiver(sender, **kwargs):
    print("Signal received. Processing starts.")
    time.sleep(5)  # Introduces a 5 second delay
    print("Signal processing completed.")

# Somewhere in your views or other logic
def my_view(request):
    print("Before sending signal.")
    my_signal.send(sender=None)
    print("After sending signal.")
