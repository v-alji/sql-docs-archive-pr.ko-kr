---
title: sqlcmd를 사용하여 Transact-SQL 스크립트 파일 실행
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: rothja
ms.author: jroth
ms.openlocfilehash: cd34b089fc4e971cac9e5713cbe303192a7a48c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647583"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a><span data-ttu-id="f6ec1-102">sqlcmd를 사용하여 Transact-SQL 스크립트 파일 실행</span><span class="sxs-lookup"><span data-stu-id="f6ec1-102">Run Transact-SQL Script Files Using sqlcmd</span></span>
  <span data-ttu-id="f6ec1-103">`sqlcmd`를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-103">You can use `sqlcmd` to run a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="f6ec1-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문, `sqlcmd` 명령 및 스크립팅 변수의 조합을 포함할 수 있는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-104">A [!INCLUDE[tsql](../../includes/tsql-md.md)] script file is a text file that can contain a combination of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="f6ec1-105">메모장을 사용하여 간단한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일을 만들려면 다음 단계를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-105">To create a simple [!INCLUDE[tsql](../../includes/tsql-md.md)] script file by using Notepad, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f6ec1-106">**시작**을 클릭하고 **모든 프로그램**, **보조프로그램**을 차례로 가리킨 다음 **메모장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-106">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Notepad**.</span></span>  
  
2.  <span data-ttu-id="f6ec1-107">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 복사하여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-107">Copy and paste the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code into Notepad:</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  <span data-ttu-id="f6ec1-108">C 드라이브에 **myScript.sql** 이라는 이름으로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-108">Save the file as **myScript.sql** in the C drive.</span></span>  
  
### <a name="to-run-the-script-file"></a><span data-ttu-id="f6ec1-109">스크립트 파일을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="f6ec1-109">To run the script file</span></span>  
  
1.  <span data-ttu-id="f6ec1-110">명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-110">Open a command prompt window.</span></span>  
  
2.  <span data-ttu-id="f6ec1-111">명령 프롬프트 창에서 `sqlcmd -S myServer\instanceName -i C:\myScript.sql`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-111">In the Command Prompt window, type: `sqlcmd -S myServer\instanceName -i C:\myScript.sql`</span></span>  
  
3.  <span data-ttu-id="f6ec1-112">Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-112">Press ENTER.</span></span>  
  
 <span data-ttu-id="f6ec1-113">명령 프롬프트 창에 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 직원의 이름 및 주소 목록이 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-113">A list of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] employee names and addresses is written to the command prompt window.</span></span>  
  
### <a name="to-save-this-output-to-a-text-file"></a><span data-ttu-id="f6ec1-114">텍스트 파일에 이 출력을 저장하려면</span><span class="sxs-lookup"><span data-stu-id="f6ec1-114">To save this output to a text file</span></span>  
  
1.  <span data-ttu-id="f6ec1-115">명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-115">Open a command prompt window.</span></span>  
  
2.  <span data-ttu-id="f6ec1-116">명령 프롬프트 창에서 `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-116">In the Command Prompt window, type: `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`</span></span>  
  
3.  <span data-ttu-id="f6ec1-117">Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-117">Press ENTER.</span></span>  
  
 <span data-ttu-id="f6ec1-118">출력이 명령 프롬프트 창에 반환되는 대신</span><span class="sxs-lookup"><span data-stu-id="f6ec1-118">No output is returned in the Command Prompt window.</span></span> <span data-ttu-id="f6ec1-119">EmpAdds.txt 파일에 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-119">Instead, the output is sent to the EmpAdds.txt file.</span></span> <span data-ttu-id="f6ec1-120">EmpAdds.txt 파일을 열어서 이 출력을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ec1-120">You can verify this output by opening the EmpAdds.txt file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ec1-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6ec1-121">See Also</span></span>  
 <span data-ttu-id="f6ec1-122">[sqlcmd 유틸리티 시작](sqlcmd-start-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f6ec1-122">[Start the sqlcmd Utility](sqlcmd-start-the-utility.md) </span></span>  
 [<span data-ttu-id="f6ec1-123">sqlcmd 유틸리티</span><span class="sxs-lookup"><span data-stu-id="f6ec1-123">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
  
