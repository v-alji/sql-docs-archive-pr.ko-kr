---
title: Transact-SQL의 OLE 자동화 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], OLE Automation
- batches [SQL Server], OLE Automation
- OLE Automation [SQL Server]
- OLE Automation [SQL Server], about OLE Automation
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f36846565bb60fbf875e9babdabbb6d1667f5ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661632"
---
# <a name="ole-automation-objects-in-transact-sql"></a><span data-ttu-id="063eb-102">Transact-SQL의 OLE 자동화 개체</span><span class="sxs-lookup"><span data-stu-id="063eb-102">OLE Automation Objects in Transact-SQL</span></span>
  [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="063eb-103">에는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리, 저장 프로시저 및 트리거를 통해 OLE 자동화 개체를 참조할 수 있도록 하는 몇 가지 시스템 저장 프로시저가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-103">includes several system stored procedures that allow OLE Automation objects to be referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] batches, stored procedures, and triggers.</span></span> <span data-ttu-id="063eb-104">이러한 시스템 저장 프로시저는 확장 저장 프로시저처럼 실행되며 저장 프로시저를 통해 실행되는 OLE 자동화 개체는 확장 저장 프로시저와 같은 방식으로 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스의 주소 공간에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-104">These system stored procedures run as extended stored procedures, and the OLE Automation objects that are executed through the stored procedures run in the address space of an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in the same way that an extended stored procedure runs.</span></span>  
  
 <span data-ttu-id="063eb-105">OLE Automation 저장 프로시저를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리에서 **IDispatch** 인터페이스를 제공하는 개체와 같은 사용자 지정 OLE Automation 개체와 SQL-DMO 개체를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-105">The OLE Automation stored procedures enable [!INCLUDE[tsql](../../includes/tsql-md.md)] batches to reference SQL-DMO objects and custom OLE Automation objects, such as objects that expose the **IDispatch** interface.</span></span> <span data-ttu-id="063eb-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]를 사용하여 만들어진 사용자 지정 종속 프로세스 OLE 서버에는 **Class_Initialize** 및 **Class_Terminate** 서브루틴에 대한 오류 처리기(**On Error GoTo** 문으로 지정)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-106">A custom in-process OLE server that is created by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] must have an error handler (specified with the **On Error GoTo** statement) for the **Class_Initialize** and **Class_Terminate** subroutines.</span></span> <span data-ttu-id="063eb-107">**Class_Initialize** 및 **Class_Terminate** 서브루틴의 오류가 처리되지 않을 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스의 액세스 위반과 같은 예상치 못한 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-107">Unhandled errors in the **Class_Initialize** and **Class_Terminate** subroutines can cause unpredictable errors, such as an access violation in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="063eb-108">또한 다른 서브루틴에 대한 오류 처리기도 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-108">Error handlers for other subroutines are also recommended.</span></span>  
  
 <span data-ttu-id="063eb-109">[!INCLUDE[tsql](../../includes/tsql-md.md)]의 OLE Automation 개체를 사용하려면 우선 **sp_OACreate** 시스템 저장 프로시저를 호출하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 주소 공간에 개체의 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-109">The first step when using an OLE Automation object in [!INCLUDE[tsql](../../includes/tsql-md.md)] is to call the **sp_OACreate** system stored procedure to create an instance of the object in the address space of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="063eb-110">개체의 인스턴스가 생성된 후에는 다음과 같은 저장 프로시저를 호출하여 개체의 속성, 메서드 및 개체 관련 오류 정보에 대한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-110">After an instance of the object has been created, call the following stored procedures to work with the properties, methods, and error information related to the object:</span></span>  
  
-   <span data-ttu-id="063eb-111">속성 값을 가져오는**sp_OAGetProperty**</span><span class="sxs-lookup"><span data-stu-id="063eb-111">**sp_OAGetProperty** obtains the value of a property.</span></span>  
  
-   <span data-ttu-id="063eb-112">속성 값을 설정하는**sp_OASetProperty**</span><span class="sxs-lookup"><span data-stu-id="063eb-112">**sp_OASetProperty** sets the value of a property.</span></span>  
  
-   <span data-ttu-id="063eb-113">메서드를 호출하는**sp_OAMethod**</span><span class="sxs-lookup"><span data-stu-id="063eb-113">**sp_OAMethod** calls a method.</span></span>  
  
-   <span data-ttu-id="063eb-114">최신 오류 정보를 가져오는**sp_OAGetErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="063eb-114">**sp_OAGetErrorInfo** obtains the most recent error information.</span></span>  
  
 <span data-ttu-id="063eb-115">개체가 더 이상 필요하지 않을 때는 **sp_OADestroy** 를 호출하여 **sp_OACreate**로 생성된 개체의 인스턴스를 할당 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-115">When there is no more need for the object, call **sp_OADestroy** to deallocate the instance of the object created by using **sp_OACreate**.</span></span>  
  
 <span data-ttu-id="063eb-116">OLE 자동화 개체는 속성 값과 메서드를 통해 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-116">OLE Automation objects return data through property values and methods.</span></span> <span data-ttu-id="063eb-117">**sp_OAGetProperty** 및 **sp_OAMethod** 는 결과 집합의 형식으로 이러한 데이터 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-117">**sp_OAGetProperty** and **sp_OAMethod** return these data values in the form of a result set.</span></span>  
  
 <span data-ttu-id="063eb-118">OLE Automation 개체의 범위는 일괄 처리입니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-118">The scope of an OLE Automation object is a batch.</span></span> <span data-ttu-id="063eb-119">개체의 모든 참조는 하나의 일괄 처리, 저장 프로시저 또는 트리거 안에 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-119">All references to the object must be contained in a single batch, stored procedure, or trigger.</span></span>  
  
 <span data-ttu-id="063eb-120">개체를 참조할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE 자동화 개체는 참조되는 개체 안에 포함된 다른 개체들 간의 순회 검색을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-120">When it references objects, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE Automation objects support traversing the referenced object to other objects that it contains.</span></span> <span data-ttu-id="063eb-121">예를 들어 SQL-DMO **SQLServer** 개체를 사용할 때 해당 서버에 포함된 데이터베이스와 테이블에 대한 참조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="063eb-121">For example, when using the SQL-DMO **SQLServer** object, references can be made to databases and tables contained on that server.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="063eb-122">관련 내용</span><span class="sxs-lookup"><span data-stu-id="063eb-122">Related Content</span></span>  
 [<span data-ttu-id="063eb-123">개체 계층 구조 구문&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="063eb-123">Object Hierarchy Syntax &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql)  
  
 [<span data-ttu-id="063eb-124">노출 영역 구성</span><span class="sxs-lookup"><span data-stu-id="063eb-124">Surface Area Configuration</span></span>](../security/surface-area-configuration.md)  
  
 [<span data-ttu-id="063eb-125">Ole Automation Procedures 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="063eb-125">Ole Automation Procedures Server Configuration Option</span></span>](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
 [<span data-ttu-id="063eb-126">sp_OACreate&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="063eb-126">sp_OACreate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oacreate-transact-sql)  
  
 [<span data-ttu-id="063eb-127">sp_OAGetProperty&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="063eb-127">sp_OAGetProperty &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql)  
  
 [<span data-ttu-id="063eb-128">sp_OASetProperty&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="063eb-128">sp_OASetProperty &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql)  
  
 [<span data-ttu-id="063eb-129">sp_OAMethod&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="063eb-129">sp_OAMethod &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oamethod-transact-sql)  
  
 [<span data-ttu-id="063eb-130">sp_OAGetErrorInfo&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="063eb-130">sp_OAGetErrorInfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
 [<span data-ttu-id="063eb-131">sp_OADestroy&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="063eb-131">sp_OADestroy &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oadestroy-transact-sql)  
  
  
