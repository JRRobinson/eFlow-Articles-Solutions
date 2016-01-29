# **eFlow 5 - Change Validation message by code** #

## **Question / Description** ##

I know the validation message is save at vFunction message property in Visual Designer.

Did anyone know how can I change the message by code?

![](http://i.imgur.com/Ecs2dtX.jpg)


## **Answer / Solution** ##

Try this but do note that if the same field has multiple validations then the last one that failed the validation, its message will be shown.  It is alright since after user corrects it then the next last invalid msg will be shown.

        #region SetErrorMessage
        /// <summary>
        /// 
        /// </summary>
        /// <param name="csm"></param>
        /// <param name="fieldData"></param>
        /// <param name="validateResult"></param>
        private static void SetErrorMessage(ITisClientServicesModule oCSM, ITisFieldData fieldData, string errorMessage)
        {
            if (string.IsNullOrEmpty(errorMessage))
                return;

            ITisFlowParams flowParams = oCSM.Setup.get_Flow(fieldData.ParentCollection.FlowType);
            ITisFieldParams fieldParams = flowParams.get_Field(fieldData.SetupField.Name);
            ITisRuleParams ruleParams = fieldParams.LinkedRules.GetByIndex(0);
            if (ruleParams != null) ruleParams.Miscellaneous.InvalidMessage = errorMessage;
        }
        #endregion SetErrorMessage









