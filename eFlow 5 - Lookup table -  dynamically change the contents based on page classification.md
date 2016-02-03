# **eFlow 5 - Lookup table -  dynamically change the contents based on page classification** #

## **Question / Description** ##

We have a situation where we would like to set the contents of a lookup table based on a classification provided for the page by Smart/Script or Manually. In summary we will have a lookup table  with some default values, but based on the classification we want to clear this lookuptable and populate it again with some data based on the Classification.

Is it possible to do this? It will work on Validate and on WebValidate?

Other suggestions to have this functionality will be welcome too. Sample codes will be more than welcome.

## **Answer / Solution** ##

The code should be something like this: 
 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Forms;
 
using TiS.Core.Application.Events.Station;
using TiS.Core.Application.Workflow;
using TiS.Core.Application.Workflow.WFCommon;
using TiS.Core.Application.DataModel.Dynamic;
using TiS.Core.Application.Interfaces;
using TiS.Core.Application.DataModel.Setup;
using TiS.Core.Application.DbAccess;
using TiS.Core.TisCommon;
 
namespace Demo
{
    class LookupTables : TiS.Core.Application.Events.Setup.Adapters.LookupTableEventsAdapter
    {
        public override void OnPostQuery(ITisClientServicesModule csm, IList<ITisFieldData> fieldsData, ref ITisDbQueryResult queryResult)
        {
            MessageBox.Show("OnPostQuery");
        }
 
        public override void OnPreQuery(ITisClientServicesModule csm, IList<ITisFieldData> fieldsData, bool validationOnly, out string queryWhereClause)
        {
            queryWhereClause = "";
            MessageBox.Show("OnPreQuery");
        }
    }
}
 
--------------------------
 
then the events in the Designer should be something like: 
Demo:LookupTables:OnPostQuery
Demo:LookupTables:OnPreQuery






