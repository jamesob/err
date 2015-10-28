Scheduling
==========


Calling a function at a regular interval
----------------------------------------

It's possible to automatically call functions at regular intervals,
using the :meth:`~errbot.botplugin.BotPlugin.start_poller` and
:meth:`~errbot.botplugin.BotPlugin.stop_poller` methods.

For example, you could schedule a callback to be executed once every
minute when your plugin gets activated:

.. code-block:: python
   :emphasize-lines: 10

    from errbot import BotPlugin

    class PluginExample(BotPlugin):
        def my_callback(self):
            self.log.debug('I am called every minute')

        def activate(self):
            super().activate()
            self.start_poller(60, self.my_callback)
