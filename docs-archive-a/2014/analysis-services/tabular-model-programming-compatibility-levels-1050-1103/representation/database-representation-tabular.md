---
title: 데이터베이스 표현 (테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 16a233fb-f83b-4ca1-acb5-6186eca0a62c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c327e07685e98e6fa9f992025510e869d909e5ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649226"
---
# <a name="database-representationtabular"></a><span data-ttu-id="2a345-102">데이터베이스 표현(테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="2a345-102">Database Representation(Tabular)</span></span>
  <span data-ttu-id="2a345-103">테이블 형식 모드에서 데이터베이스는 테이블 형식 모델의 모든 개체에 대한 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-103">In Tabular Mode, the database is the container for all objects in the tabular model.</span></span>  
  
## <a name="database-representation"></a><span data-ttu-id="2a345-104">데이터베이스 표현</span><span class="sxs-lookup"><span data-stu-id="2a345-104">Database Representation</span></span>  
 <span data-ttu-id="2a345-105">데이터베이스는 테이블 형식 모델을 형성하는 모든 개체가 있는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-105">The database is the place where all objects that form a tabular model reside.</span></span> <span data-ttu-id="2a345-106">개발자는 데이터베이스에 포함된 연결, 테이블, 역할 등의 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-106">Contained by the database, the developer finds objects like connections, tables, roles and many more.</span></span>  
  
### <a name="database-in-amo"></a><span data-ttu-id="2a345-107">AMO의 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="2a345-107">Database in AMO</span></span>  
 <span data-ttu-id="2a345-108">AMO를 사용하여 테이블 형식 모델 데이터베이스를 관리하는 경우 AMO의 <xref:Microsoft.AnalysisServices.Database> 개체는 테이블 형식 모델의 데이터베이스 논리 개체에 일 대 일로 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-108">When using AMO to manage a tabular model database, the <xref:Microsoft.AnalysisServices.Database> object in AMO matches one-to-one the database logical object in a tabular model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a345-109">AMO에서 사용자가 데이터베이스 개체에 액세스하려면 서버 개체에 대한 액세스 권한을 가지고 해당 개체에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-109">In order to gain access to a database object, in AMO, the user needs to have access to a server object and connect to it.</span></span>  
  
### <a name="database-in-adomdnet"></a><span data-ttu-id="2a345-110">ADOMD.Net의 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="2a345-110">Database in ADOMD.Net</span></span>  
 <span data-ttu-id="2a345-111">ADOMD를 사용하여 테이블 형식 모델 데이터베이스를 확인하고 쿼리하는 경우 특정 데이터베이스에 대한 연결은 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 개체를 통해 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-111">When using ADOMD to consult and query a tabular model database, connection to a specific database is obtained through the <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> object.</span></span>  
  
 <span data-ttu-id="2a345-112">다음 코드 조각을 사용하여 특정 데이터베이스에 직접 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-112">You can connect directly to a certain database using the following code snippet:</span></span>  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
...  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
...  
  
```  
  
 <span data-ttu-id="2a345-113">또한 닫히지 않은 기존 연결 개체에 대해 다음 코드에서와 같이 현재 데이터베이스를 다른 데이터베이스로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-113">Also, over an existing connection object (that hasn't been closed), you can change the current database to another as shown in the following code snippet:</span></span>  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a><span data-ttu-id="2a345-114">AMO의 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="2a345-114">Database in AMO</span></span>  
 <span data-ttu-id="2a345-115">AMO를 사용하여 데이터베이스 개체를 관리할 때는 먼저 <xref:Microsoft.AnalysisServices.Server> 개체로 시작하여</span><span class="sxs-lookup"><span data-stu-id="2a345-115">When using AMO to manage a database object, start with a <xref:Microsoft.AnalysisServices.Server> object.</span></span> <span data-ttu-id="2a345-116">데이터베이스 컬렉션에서 데이터베이스를 검색하거나 새 데이터베이스를 컬렉션에 추가하여 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-116">Then search for your database in the databases collection or create a new database by adding one to the collection.</span></span>  
  
 <span data-ttu-id="2a345-117">다음 코드 조각에서는 데이터베이스가 존재 하지 않는지 확인 한 후 서버에 연결 하 고 빈 데이터베이스를 만드는 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-117">The following code snippet shows the steps to connect to a server and create an empty database, after checking the database doesn't exist:</span></span>  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 <span data-ttu-id="2a345-118">AMO를 사용 하 여 데이터베이스 표현을 만들고 조작 하는 방법에 대 한 실질적인 이해는 테이블 형식 AMO 2012 샘플의 소스 코드를 참조 하세요. 특히 다음 원본 파일을 확인 하십시오. Database.cs.</span><span class="sxs-lookup"><span data-stu-id="2a345-118">For a practical understanding on how to use AMO to create and manipulate database representations, see source code in the Tabular AMO 2012 sample; specifically check in the following source file: Database.cs.</span></span> <span data-ttu-id="2a345-119">예제 코드는 여기에서 설명한 논리적 개념에 대한 지원으로만 제공되며 프로덕션 환경에서 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a345-119">Sample code is provided only as a support to the logical concepts explained here, and should not be used in a production environment.</span></span>  
  
  
