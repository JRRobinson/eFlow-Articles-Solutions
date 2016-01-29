## eFlow 4.5 - VS2012 debugger does not step in custom code ##


### Question/ description: ###
I noticed that VS2012 debugger has problem stepping in custom code when process is started from VS itself.

It can attach to the process or be started by Debugger.Launch(). is there a way to make it work?

eFlow 4.5 SP4


### Answer: ###

I found solution.

1. Create config file in the bin folder(efExport.config)
2. Put this inside

        <?xml version="1.0"?>
    	<configuration>
    		<startup>
    			<supportedRuntime version="v2.0.50727"/>
    		</startup>
    	</configuration>
