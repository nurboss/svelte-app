<div class="overflow-x-auto rounded-md">
    <table class="min-w-full bg-white border  border-gray-200 rounded-md">
      <thead>
        <tr class="text-sm ">
           
            <th class="p-5 text-gray-700 font-sans">
              Flag
            </th>
            <th class="p-5 text-gray-700 text-start font-sans">
              Name
            </th>
            <th class="p-5 text-gray-700 text-start font-sans">
              Population
            </th>
            <th class="p-5 text-gray-700 text-start font-sans">
              CIOC
            </th>
            <th class="p-5 text-gray-700 text-start font-sans">
              UN Member Status
            </th>
            <th class="p-5 text-gray-700 text-start font-sans">
                Currencies(Key)
            </th>
            <th class="p-5 text-gray-700 text-start font-sans">
              Languages
            </th>
          </tr>
      </thead>
      <tbody>
        {#each Array.from(Array(10).keys()) as row (row)}
              <tr class="border-t border-gray-200">
                <td class="p-5 ">
                  <div class="animate-pulse">
                    <div class="w-8 h-6 bg-gray-300 rounded-md"></div>
                  </div>
                </td>
                <td class="p-4 font-medium text-gray-500 font-sans">
                  <div class="animate-pulse flex justify-center items-center">
                    <div class="w-20 h-3 bg-gray-300 rounded-sm"></div>
                  </div>
                </td>
                <td class="p-4 font-medium text-gray-500 font-sans">
                  <div class="animate-pulse flex justify-center items-center">
                    <div class="w-12 h-3 bg-gray-300 rounded-sm"></div>
                  </div>
                </td>
                <td class="p-4 font-medium text-gray-500 font-sans text-center">
                  <div class="animate-pulse flex justify-center items-center">
                    <div class="w-10 h-3 bg-gray-300 "></div>
                  </div>
                </td>
                <td class="p-4 text-center font-medium text-gray-500 font-sans">
                  <div class="animate-pulse flex justify-center items-center">
                    <div class="w-8 h-5 bg-gray-300 rounded-md"></div>
                  </div>
                </td>
                <td class="p-4 text-center font-medium text-gray-500 font-sans">
                  <div class="animate-pulse flex justify-center items-center">
                    <div class="w-14 h-3 bg-gray-300 rounded-sm"></div>
                  </div>
                </td>
                <td class="p-4 font-medium text-gray-500 font-sans">
                  <div class="animate-pulse flex justify-center items-center">
                    <div class="w-14 h-3 bg-gray-300 rounded-sm"></div>
                  </div>
                </td>
              </tr>
          {/each}
      </tbody>
    </table>
  </div>