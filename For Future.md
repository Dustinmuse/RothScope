# For Future Developers

This is for the future developers who may work on this project. This shows all the known issue we have found and didn't have the time to fix. There is also improvements we didn't have the time to do, that would make the software better.

## Known Issues

- If you loss internet during optimization process it will not restore baseline to the scenario you are running the optimization on

- The "Roth Balance", "Tax-Deferred", "Tax-Rate" columns in the Year-By-Yeay Breakdown Table in the OptimizationResults.vue component/page are not being filled in from the API and the boxes in those columns are filled in with a "-" (null values)

## Improvements for Future Teams

- Lock all inputs from the user during the optimization process, besides the back button on the ChoosingOptimization.vue component/page

- Add more/better exception handling during the optimization process

- Add a sorting for the client's and scenario's list

- Try to speed up the amount of time it takes from when the optimization starts to when it displays the data on the OptimizationResults.vue component/page
