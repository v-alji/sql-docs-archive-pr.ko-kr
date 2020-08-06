---
title: 연결 표현 (테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 4b410b16-d36e-4185-bb20-922e66e5e2b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 60f3fdc10baf5dc3be9cd1b0ee6196d2a8da3d2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649228"
---
# <a name="connection-representation-tabular"></a><span data-ttu-id="5d548-102">연결 표현(테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="5d548-102">Connection Representation (Tabular)</span></span>
  <span data-ttu-id="5d548-103">연결 개체는 테이블 형식 모델을 채우는 데이터의 원본을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5d548-103">The connection object defines the source of the data that populates the tabular model.</span></span>  
  
## <a name="connection-representation"></a><span data-ttu-id="5d548-104">연결 표현</span><span class="sxs-lookup"><span data-stu-id="5d548-104">Connection Representation</span></span>  
 <span data-ttu-id="5d548-105">연결 개체의 사양은 OLE DB 공급자의 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="5d548-105">The specification for the connection object follows the rules of OLE DB providers.</span></span>  
  
### <a name="connection-in-amo"></a><span data-ttu-id="5d548-106">AMO의 연결</span><span class="sxs-lookup"><span data-stu-id="5d548-106">Connection in AMO</span></span>  
 <span data-ttu-id="5d548-107">AMO를 사용하여 테이블 형식 모델 데이터베이스를 관리하는 경우 AMO의 <xref:Microsoft.AnalysisServices.DataSource> 개체는 연결 논리 개체에 일 대 일로 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d548-107">When using AMO to manage a tabular model database, the <xref:Microsoft.AnalysisServices.DataSource> object in AMO matches one-to-one to the connection logical object.</span></span>  
  
 <span data-ttu-id="5d548-108">다음 코드 조각에서는 AMO 데이터 원본 또는 테이블 형식 모델의 Connection 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5d548-108">The following code snippet shows how to create an AMO data source, or Connection object in a tabular model.</span></span>  
  
```  
  
//Create an OLEDB connection string  
StringBuilder SqlCnxStr = new StringBuilder();  
SqlCnxStr.Append(String.Format("Data Source={0};" ,SQLServer.Text));  
SqlCnxStr.Append(String.Format("Initial Catalog={0};", SQLDatabase.Text));  
SqlCnxStr.Append(String.Format("Persist Security Info={0};", false));  
SqlCnxStr.Append(String.Format("Integrated Security={0};", "SSPI"));  
SqlCnxStr.Append(String.Format("Provider={0}", "SQLNCLI11"));  
String DatasourceCnxString = SqlCnxStr.ToString();  
  
//Verify connection string and connectivity  
System.Data.OleDb.OleDbConnection OleDbCnx = new System.Data.OleDb.OleDbConnection(DatasourceCnxString);  
try  
{  
    OleDbCnx.Open();  
}  
catch ()  
{  
    throw;  
}  
String newDataSourceName = (string.IsNullOrEmpty(DataSourceName.Text) || string.IsNullOrWhiteSpace(DataSourceName.Text)) ? SQLDatabase.Text : DataSourceName.Text;  
AMO.DataSource newDatasource = newDatabase.DataSources.Add(newDataSourceName, newDataSourceName);  
newDatasource.ConnectionString = DatasourceCnxString.Text;  
if (impersonateServiceAccount.Checked)  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateServiceAccount);  
else  
{  
    if (String.IsNullOrEmpty(impersonateAccountUserName.Text))  
    {  
        MessageBox.Show(String.Format("Account User Name cannot be blank when using 'ImpersonateAccount' mode"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        return;  
    }  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateAccount, impersonateAccountUserName.Text, impersonateAccountPassword.Text);  
}  
newDatasource.Update();  
  
```  
  
## <a name="tabular-amo-2012-sample"></a><span data-ttu-id="5d548-109">Tabular AMO 2012 예제</span><span class="sxs-lookup"><span data-stu-id="5d548-109">Tabular AMO 2012 sample</span></span>  
 <span data-ttu-id="5d548-110">AMO를 사용하여 연결 표현을 만들고 조작하려면 Tabular AMO 2012 예제의 원본 코드를 참조하십시오. 특히 다음 원본 파일을 확인하십시오. 특히 원본 파일 Database.cs에서 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="5d548-110">To have a better understanding on how to use AMO to create and manipulate connection representations, see source code in the Tabular AMO 2012 sample; specifically check in the following source file: Database.cs.</span></span> <span data-ttu-id="5d548-111">예제는 Codeplex에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d548-111">The sample is available at Codeplex.</span></span> <span data-ttu-id="5d548-112">예제 코드는 여기에서 설명한 논리적 개념에 대한 지원으로만 제공되며 프로덕션 환경에서 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d548-112">Sample code is provided only as a support to the logical concepts explained here, and should not be used in a production environment.</span></span>  
  
  
