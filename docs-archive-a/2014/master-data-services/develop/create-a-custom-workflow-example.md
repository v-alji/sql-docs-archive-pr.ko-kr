---
title: 사용자 지정 워크플로 예제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ee9d6e18bf4e54ae5eb6af6a56494fff0db28684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728407"
---
# <a name="custom-workflow-example-master-data-services"></a><span data-ttu-id="e9a5d-102">사용자 지정 워크플로 예제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e9a5d-102">Custom Workflow Example (Master Data Services)</span></span>
  <span data-ttu-id="e9a5d-103">에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 사용자 지정 워크플로 클래스 라이브러리를 만들 때 MasterDataServices를 구현 하는 클래스를 만듭니다. [iworkflowtypeextender](/previous-versions/sql/sql-server-2016/hh758785(v=sql.130)) 인터페이스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a5d-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], when you create a custom workflow class library, you create a class that implements the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender](/previous-versions/sql/sql-server-2016/hh758785(v=sql.130)) interface.</span></span> <span data-ttu-id="e9a5d-104">이 인터페이스에는 워크플로가 시작 될 때 MDS 워크플로 통합 서비스 SQL Server에서 호출 하는 [MasterDataServices](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))메서드 하나가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a5d-104">This interface includes one method, [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)), that is called by SQL Server MDS Workflow Integration Service when a workflow starts.</span></span> <span data-ttu-id="e9a5d-105">[MasterDataServices](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) 에는 두 개의 매개 변수가 포함 됩니다. *workflowType* 에는의 **워크플로 유형** 텍스트 상자에 입력 한 텍스트가 포함 되 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 고 *dataelement* 에는 워크플로 비즈니스 규칙을 트리거한 항목에 대 한 메타 데이터 및 항목 데이터가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a5d-105">The [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) method contains two parameters: *workflowType* contains the text you entered in the **Workflow type** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], and *dataElement* contains metadata and item data for the item that triggered the workflow business rule.</span></span>  
  
## <a name="custom-workflow-example"></a><span data-ttu-id="e9a5d-106">사용자 지정 워크플로 예제</span><span class="sxs-lookup"><span data-stu-id="e9a5d-106">Custom Workflow Example</span></span>  
 <span data-ttu-id="e9a5d-107">다음 코드 예제에서는 [MasterDataServices 워크플로 \*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) 메서드를 구현 하 여 워크플로 비즈니스 규칙을 트리거한 요소의 XML 데이터에서 Name, Code 및 LastChgUserName 특성을 추출 하는 방법 및 저장 프로시저를 호출 하 여 다른 데이터베이스에 삽입 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e9a5d-107">The following code example shows how you how to implement the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) method to extract the Name, Code, and LastChgUserName attributes from the XML data for the element that triggered the workflow business rule, and how to call a stored procedure to insert them into another database.</span></span> <span data-ttu-id="e9a5d-108">항목 데이터 XML의 예와 항목 데이터 XML에 포함되는 태그에 대한 설명은 [사용자 지정 워크플로 XML 설명&#40;Master Data Services&#41;](create-a-custom-workflow-xml-description.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9a5d-108">For an example of the item data XML and an explanation of the tags it contains, see [Custom Workflow XML Description &#40;Master Data Services&#41;](create-a-custom-workflow-xml-description.md).</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9a5d-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9a5d-109">See Also</span></span>  
 [<span data-ttu-id="e9a5d-110">사용자 지정 워크플로 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9a5d-110">Create a Custom Workflow &#40;Master Data Services&#41;</span></span>](create-a-custom-workflow-master-data-services.md)  
  
  
