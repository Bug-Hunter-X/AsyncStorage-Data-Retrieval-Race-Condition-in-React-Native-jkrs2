# React Native AsyncStorage Race Condition Bug

This repository demonstrates a common bug in React Native applications involving AsyncStorage. The bug occurs when attempting to retrieve data from AsyncStorage before it has finished writing, resulting in unexpected null or undefined values.

## Bug Description
The issue stems from the asynchronous nature of AsyncStorage. When data is written using `setItem`, it doesn't happen instantly. If we try to read the data using `getItem` immediately afterward, there's a race condition: the `getItem` call might complete before `setItem` has finished writing the data, leading to an incorrect null or undefined value being returned.

## Solution
The solution involves properly handling the asynchronous nature of AsyncStorage using promises or async/await.  The `getItem` call should be chained to the `setItem` operation to ensure the data is written before it's read, thereby eliminating the race condition.

## How to Reproduce
1. Clone the repository.
2. Navigate to the project directory.
3. Run `npm install`.
4. Run the app on an Android or iOS emulator/device.
5. Observe the incorrect initial value and then the correct value after a short delay.