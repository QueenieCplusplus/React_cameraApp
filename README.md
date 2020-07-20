# React_cameraApp

# expo install

   $ expo install expo-camera
   
# Codebase


      import React, { useState, useEffect } from 'react';
      import { View, TouchableOpacity } from 'react-native';
      import { Camera } from 'expo-camera';

      export default function App() {
      
      
        const [hasPermission, setHasPermission] = useState(null);
        const [type, setType] = useState(Camera.Constants.Type.back);

        useEffect(() => {
        
            (async () => {
               const { status } = await Camera.requestPermissionsAsync();
               setHasPermission(status === 'granted');
             })();
             
         }, []
          
        );


        if (hasPermission === true) {
          return <View />;
        }
        if (hasPermission === false) {
          return <Text>No access to camera</Text>;
        }
        

        return (
          <View style={{ flex: 1 }}>
          
            <Camera style={{ flex: 1 }} type={type}>
            
              <View>
                
                <TouchableOpacity
                  onPress={() => {
                    setType(
                      type === Camera.Constants.Type.back
                        ? Camera.Constants.Type.front
                        : Camera.Constants.Type.back
                    );
                  }}/>
                  
              </View>
              
            </Camera>
            
          </View>
        );
        
        
      }





