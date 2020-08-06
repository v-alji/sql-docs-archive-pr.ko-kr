---
title: 데이터베이스 개체에 대한 액세스 권한 부여
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 22bd0bb1f01e59ec30f7cf1bbf128c890d3d5d64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660238"
---
# <a name="granting-access-to-a-database-object"></a><span data-ttu-id="bc6c3-102">데이터베이스 개체에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="bc6c3-102">Granting Access to a Database Object</span></span>
  <span data-ttu-id="bc6c3-103"> 관리자는 **Products** 테이블 및 **vw_Names** 뷰에서 SELECT를 실행하고 **pr_Names** 프로시저를 실행할 수 있지만 Mary는 이러한 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-103">As an administrator, you can execute the SELECT from the **Products** table and the **vw_Names** view, and execute the **pr_Names** procedure; however, Mary cannot.</span></span> <span data-ttu-id="bc6c3-104">Mary에게 필요한 사용 권한을 부여하려면 GRANT 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-104">To grant Mary the necessary permissions, use the GRANT statement.</span></span>  
  
### <a name="procedure-title"></a><span data-ttu-id="bc6c3-105">절차 제목</span><span class="sxs-lookup"><span data-stu-id="bc6c3-105">Procedure Title</span></span>  
  
1.  <span data-ttu-id="bc6c3-106">다음 문을 실행하여 `Mary` 저장 프로시저에 대한 `EXECUTE` 권한을 `pr_Names` 에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-106">Execute the following statement to give `Mary` the `EXECUTE` permission for the `pr_Names` stored procedure.</span></span>  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 <span data-ttu-id="bc6c3-107">이 시나리오에서 Mary는 이 저장 프로시저를 사용하여 **Products** 테이블에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-107">In this scenario, Mary can only access the **Products** table by using the stored procedure.</span></span> <span data-ttu-id="bc6c3-108">Mary가 SELECT 문을 뷰에 대해 실행할 수 있도록 하려면 또한 `GRANT SELECT ON vw_Names TO Mary`를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-108">If you want Mary to be able to execute a SELECT statement against the view, then you must also execute `GRANT SELECT ON vw_Names TO Mary`.</span></span> <span data-ttu-id="bc6c3-109">데이터베이스 개체에 대한 액세스 권한을 제거하려면 REVOKE 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-109">To remove access to database objects, use the REVOKE statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc6c3-110">테이블, 뷰 및 저장 프로시저를 동일한 스키마에서 소유하지 않을 경우 사용 권한을 부여하는 것은 더 복잡해집니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-110">If the table, the view, and the stored procedure are not owned by the same schema, granting permissions becomes more complex.</span></span>  
  
## <a name="about-grant"></a><span data-ttu-id="bc6c3-111">GRANT 정보</span><span class="sxs-lookup"><span data-stu-id="bc6c3-111">About GRANT</span></span>  
 <span data-ttu-id="bc6c3-112">저장 프로시저를 실행하려면 EXECUTE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-112">You must have EXECUTE permission to execute a stored procedure.</span></span> <span data-ttu-id="bc6c3-113">데이터를 액세스 및 변경하려면 SELECT, INSERT, UPDATE 및 DELETE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-113">You must have SELECT, INSERT, UPDATE, and DELETE permissions to access and change data.</span></span> <span data-ttu-id="bc6c3-114">또한 GRANT 문은 테이블 작성 권한과 같은 다른 사용 권한에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc6c3-114">The GRANT statement is also used for other permissions, such as permission to create tables.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bc6c3-115">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="bc6c3-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bc6c3-116">요약: 데이터베이스 개체에 대한 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="bc6c3-116">Summary: Configuring Permissions on Database Objects</span></span>](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc6c3-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc6c3-117">See Also</span></span>  
 <span data-ttu-id="bc6c3-118">[GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bc6c3-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 [<span data-ttu-id="bc6c3-119">REVOKE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bc6c3-119">REVOKE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/revoke-transact-sql)  
  
  
