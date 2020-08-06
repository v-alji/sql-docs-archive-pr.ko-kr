---
title: 데이터베이스 다이어그램 디자이너 설정(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d59fa2ed197a410de6b68e388e76d2bf21c334d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734847"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a><span data-ttu-id="876c3-102">데이터베이스 다이어그램 디자이너 설정(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="876c3-102">Set Up Database Diagram Designer (Visual Database Tools)</span></span>
  <span data-ttu-id="876c3-103">데이터베이스 다이어그램 디자이너를 사용하려면 먼저 **db_owner** 역할의 멤버가 이 디자이너를 설정하여 다이어그램에 대한 액세스를 제어해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="876c3-103">To use Database Diagram Designer, it must first be set up by a member of the **db_owner** role to control access to diagrams.</span></span>  
  
### <a name="to-set-up-database-diagramming"></a><span data-ttu-id="876c3-104">데이터베이스 다이어그램을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="876c3-104">To set up database diagramming</span></span>  
  
1.  <span data-ttu-id="876c3-105">개체 탐색기에서 데이터베이스 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="876c3-105">From Object Explorer, expand a database node.</span></span>  
  
2.  <span data-ttu-id="876c3-106">데이터베이스 연결 아래에서 데이터베이스 다이어그램 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="876c3-106">Expand the Database Diagrams node under the database connection.</span></span>  
  
3.  <span data-ttu-id="876c3-107">데이터베이스 다이어그램을 설정할지 묻는 메시지가 나타나면 **예** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876c3-107">Select **Yes** when prompted if you want to set up database diagramming.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="876c3-108">이렇게 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 데이터베이스 다이어그램 테이블, 시스템 저장 프로시저 및 시스템 함수가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="876c3-108">This will create the database diagram table, system stored procedures, and a system function on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
4.  <span data-ttu-id="876c3-109">Visual Studio는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 다음 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="876c3-109">Visual Studio will create the following objects on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="876c3-110">sysdiagrams 테이블</span><span class="sxs-lookup"><span data-stu-id="876c3-110">sysdiagrams table</span></span>  
  
    2.  <span data-ttu-id="876c3-111">sp_alterdiagram 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="876c3-111">sp_alterdiagram stored procedure</span></span>  
  
    3.  <span data-ttu-id="876c3-112">sp_creatediagram 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="876c3-112">sp_creatediagram stored procedure</span></span>  
  
    4.  <span data-ttu-id="876c3-113">sp_dropdiagram 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="876c3-113">sp_dropdiagram stored procedure</span></span>  
  
    5.  <span data-ttu-id="876c3-114">sp_renamediagram 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="876c3-114">sp_renamediagram stored procedure</span></span>  
  
    6.  <span data-ttu-id="876c3-115">fn_diagramobjects 함수</span><span class="sxs-lookup"><span data-stu-id="876c3-115">fn_diagramobjects function</span></span>  
  
    7.  <span data-ttu-id="876c3-116">sp_helpdiagrams 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="876c3-116">sp_helpdiagrams stored procedure</span></span>  
  
    8.  <span data-ttu-id="876c3-117">sp_helpdiagramsdefinition 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="876c3-117">sp_helpdiagramsdefinition stored procedure</span></span>  
  
    9. <span data-ttu-id="876c3-118">sp_upgraddiagrams 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="876c3-118">sp_upgraddiagrams stored procedure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876c3-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="876c3-119">See Also</span></span>  
 <span data-ttu-id="876c3-120">[Visual Database Tools를 &#40;데이터베이스 다이어그램 소유권 이해&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="876c3-120">[Understand Database Diagram Ownership &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="876c3-121">[Visual Database Tools&#41;&#40;이전 버전에서 데이터베이스 다이어그램 업그레이드](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="876c3-121">[Upgrade Database Diagrams from Previous Editions &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="876c3-122">ALTER AUTHORIZATION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="876c3-122">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  
