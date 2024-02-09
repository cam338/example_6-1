Edited file: 
1. user_interface.cpp
  - changed the position values and the string to fit within the 2 by 16 LDC screen [within userInterfaceDisplayInit() function]
      eg. displayCharPositionWrite ( 0,0 );
          displayStringWrite( "Tmp:" ); % Tmp instead of Temperature spelled out to fit the screen
          displayCharPositionWrite ( 9,0 );
          displayStringWrite( "Gas:" );
          displayCharPositionWrite ( 0,1 );
          displayStringWrite( "Alarm:" );
  - changed the position values [within userInterfaceDisplayUpdate() function]
          sprintf(temperatureString, "%.0f", temperatureSensorReadCelsius());
          displayCharPositionWrite ( 4,0 );
          displayStringWrite( temperatureString );
          displayCharPositionWrite ( 6,0 );
          displayStringWrite( "'C" );
          displayCharPositionWrite ( 13,0 );
          if ( gasDetectorStateRead() ) {
              displayStringWrite("Detected"); % only "Det" will be shown on the screen
          } else {
              displayStringWrite( "ND" ); % changed to ND instead of Not Detected to fit the screen 
          }

Other minor edits: 
1. display.cpp
  - macro names were edited
        #define DISPLAY_16x2_LINE1_FIRST_CHARACTER_ADDRESS 0
        #define DISPLAY_16x2_LINE2_FIRST_CHARACTER_ADDRESS 64
        #define DISPLAY_16x2_LINE3_FIRST_CHARACTER_ADDRESS 20
        #define DISPLAY_16x2_LINE4_FIRST_CHARACTER_ADDRESS 84
    
