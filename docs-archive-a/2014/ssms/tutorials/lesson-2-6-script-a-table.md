---
title: 테이블 스크립팅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 247c839d83768756c57297d47f952401a1c8fd46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649296"
---
# <a name="script-a-table"></a><span data-ttu-id="f7965-102">테이블 스크립팅</span><span class="sxs-lookup"><span data-stu-id="f7965-102">Script a Table</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f7965-103">에서는 스크립트를 만들어 테이블을 선택, 삽입, 업데이트 및 삭제하고 저장 프로시저를 작성, 변경, 삭제 또는 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-103">can create scripts to select, insert, update, and delete tables, and to create, alter, drop, or execute stored procedures.</span></span>  
  
 <span data-ttu-id="f7965-104">프로시저를 삭제한 다음 프로시저를 만들거나 테이블을 만든 다음 테이블을 변경하는 등 여러 옵션이 있는 스크립트가 필요한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-104">Sometimes you want a script with multiple options, such as drop a procedure and then create a procedure, or create a table then alter a table.</span></span> <span data-ttu-id="f7965-105">조합된 스크립트를 만들려면 첫 번째 스크립트를 쿼리 편집기 창에 저장하고 두 번째 스크립트를 클립보드에 저장하여 첫 번째 스크립트 다음에 창에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-105">To create combined scripts, save the first script to a Query Editor window and the second to the clipboard so you can paste it into the window after the first script.</span></span>  
  
## <a name="creating-an-update-script"></a><span data-ttu-id="f7965-106">업데이트 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="f7965-106">Creating an Update Script</span></span>  
  
#### <a name="to-create-the-insert-script-for-a-table"></a><span data-ttu-id="f7965-107">테이블에 대한 삽입 스크립트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f7965-107">To create the insert script for a table</span></span>  
  
1.  <span data-ttu-id="f7965-108">개체 탐색기에서 사용 중인 서버를 확장하고 **데이터베이스**, [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], **테이블**을 차례로 확장한 다음 **HumanResources.Employee**를 마우스 오른쪽 단추로 클릭하고 **테이블 스크립팅**을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-108">In Object Explorer, expand your server, expand **Databases**, expand [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], expand **Tables**, right-click **HumanResources.Employee**, and then point to **Script Table As**.</span></span>  
  
2.  <span data-ttu-id="f7965-109">바로 가기 메뉴에는 **CREATE**, **DROP**, **DROP 및 CREATE**, **SELECT**, **INSERT**, **UPDATE**및 **DELETE**의 일곱 개의 스크립트 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-109">The shortcut menu has seven available scripting options: **CREATE To**, **DROP To**, **DROP and CREATE To**, **SELECT To**, **INSERT To**, **UPDATE To**, and **DELETE To**.</span></span> <span data-ttu-id="f7965-110">**UPDATE**를 가리킨 다음 **새 쿼리 편집기 창**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-110">Point to **UPDATE To**, and then click **New Query Editor Window**.</span></span>  
  
3.  <span data-ttu-id="f7965-111">새 쿼리 편집기 창이 열리고 연결이 설정된 다음 전체 Update 문이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-111">A new Query Editor window opens, makes a connection, and presents the entire update statement.</span></span>  
  
     <span data-ttu-id="f7965-112">이 연습에서는 스크립팅 기능으로 테이블 또는 저장 프로시저 만들기를 스크립팅하는 것 이상의 작업을 수행할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-112">This exercise demonstrates how the scripting feature can do more than just script the creation of a table or stored procedure.</span></span> <span data-ttu-id="f7965-113">이 새 기능을 사용하면 프로젝트에 데이터 조작 스크립트를 빠르게 추가하고 저장 프로시저를 쉽게 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-113">This new feature can help you quickly add data manipulation scripts to your project and easily script execution of stored procedures.</span></span> <span data-ttu-id="f7965-114">테이블이나 프로시저의 필드가 많을 경우 이 새 기능으로 시간을 크게 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7965-114">This can be a big timesaver for tables and procedures with many fields.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f7965-115">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="f7965-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f7965-116">요약: Transact-SQL 작성</span><span class="sxs-lookup"><span data-stu-id="f7965-116">Summary: Writing Transact-SQL</span></span>](../../tutorials/summary-writing-transact-sql.md)  
  
  
