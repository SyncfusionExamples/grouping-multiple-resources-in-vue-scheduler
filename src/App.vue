<template>
    <ejs-schedule height="600px" :selectedDate='schedulerSelectedDate'
     :eventSettings="appointmentData" :group="groupResource">
      <e-views>
        <e-view option='Day'></e-view>
        <e-view option='Week'></e-view>
        <e-view option='TimelineDay'></e-view>
        <e-view option='TimelineWeek'></e-view>
        <e-view option='Agenda'></e-view>
      </e-views>
      <e-resources>
        <e-resource :dataSource="taskDatasource" field="GroupId" title="Task Details"
        name="Tasks" textField="taskName" idField="taskId" colorField="taskColor"></e-resource>
        <e-resource :dataSource="resourceDatasource" groupIDField="taskGroupId"
        field="ResourceId" title="Resource Details" name="Resources"
        textField="personName" idField="personId" colorField="color"
        allowMultiple="true"></e-resource>
      </e-resources>
    </ejs-schedule>
</template>

<script> 
import { ScheduleComponent, Day, Week, Agenda, ResourcesDirective, ResourceDirective, 
  ViewsDirective, ViewDirective, TimelineViews } from "@syncfusion/ej2-vue-schedule";
export default {
  name: 'App',
  components: { 
    'ejs-schedule': ScheduleComponent,
    'e-views' : ViewsDirective,
    'e-view'  : ViewDirective,
    'e-resources' : ResourcesDirective,
    'e-resource'  : ResourceDirective
  },
  provide : { schedule : [ Day, Week, Agenda, TimelineViews ] },
  data() {
    return {
      schedulerSelectedDate : new Date(2022, 5, 16),
      taskDatasource : [
        {taskId: 1, taskName: "Development", taskColor: "#ffaa00"},
        {taskId: 2, taskName: 'Testing', taskColor: '#f8a398'},
        {taskId: 3, taskName: 'Support', taskColor: '#00bdae'}
      ],
      resourceDatasource : [
        {personName: 'John', personId: 1, color: '#ea7a57', taskGroupId: 1},
        {personName: 'Steve', personId: 2, color: '#357CD2', taskGroupId: 2},
        {personName: 'James', personId: 3, color: '#7fa900', taskGroupId: 2}
      ],
      groupResource : {
        byGroupID : true,
        byDate : true,
        resources : [ 'Tasks', 'Resources' ]
      },
      appointmentData : {
         dataSource : [
             {
              Id : 1,
              Subject : 'Meeting',
              StartTime: new Date(2022, 5, 13, 10, 0, 0),
              EndTime: new Date(2022, 5, 13, 11, 0, 0),
              GroupId : 1,
              ResourceId : 1
            },
            {
              Id : 2,
              Subject : 'Test Report Validation',
              StartTime: new Date(2022, 5, 17, 11, 30, 0),
              EndTime: new Date(2022, 5, 17, 12, 30, 0),
              GroupId : 2,
              ResourceId : 2
            },
            {
              Id : 3,
              Subject : 'Bug Fixing',
              StartTime: new Date(2022, 5, 15, 10, 0, 0),
              EndTime: new Date(2022, 5, 15, 11, 0, 0),
              GroupId : 3,
              ResourceId : 3
            }
         ]
      }
    };
  }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-calendars/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';
</style>
