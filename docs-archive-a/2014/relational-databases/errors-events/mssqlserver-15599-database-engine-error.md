---
title: MSSQLSERVER_15599 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 15f1b3eb6d97837f1c1c4a9944535cade5b31300
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653941"
---
# <a name="mssqlserver_15599"></a><span data-ttu-id="4bada-102">MSSQLSERVER_15599</span><span class="sxs-lookup"><span data-stu-id="4bada-102">MSSQLSERVER_15599</span></span>
    
## <a name="details"></a><span data-ttu-id="4bada-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="4bada-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4bada-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="4bada-104">Product Name</span></span>|<span data-ttu-id="4bada-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4bada-105">SQL Server</span></span>|  
|<span data-ttu-id="4bada-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="4bada-106">Event ID</span></span>|<span data-ttu-id="4bada-107">15599</span><span class="sxs-lookup"><span data-stu-id="4bada-107">15599</span></span>|  
|<span data-ttu-id="4bada-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="4bada-108">Event Source</span></span>|<span data-ttu-id="4bada-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4bada-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4bada-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4bada-110">Component</span></span>|<span data-ttu-id="4bada-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4bada-111">SQLEngine</span></span>|  
|<span data-ttu-id="4bada-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="4bada-112">Symbolic Name</span></span>|<span data-ttu-id="4bada-113">SEC_LOCAL_TEMP_AUDIT_PERMISSIONS</span><span class="sxs-lookup"><span data-stu-id="4bada-113">SEC_LOCAL_TEMP_AUDIT_PERMISSIONS</span></span>|  
|<span data-ttu-id="4bada-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="4bada-114">Message Text</span></span>|<span data-ttu-id="4bada-115">로컬 임시 개체에 대한 감사와 권한을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4bada-115">Auditing and permissions can't be set on local temporary objects.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4bada-116">설명</span><span class="sxs-lookup"><span data-stu-id="4bada-116">Explanation</span></span>  
 <span data-ttu-id="4bada-117">로컬 또는 전역 임시 개체에 대해 감사와 권한을 설정해도 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bada-117">Auditing and permissions do not have any effect when set for local or global temp objects.</span></span> <span data-ttu-id="4bada-118">문을 실행할 경우 오류가 발생하지는 않지만(작업에서 성공 결과가 반환됨) 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bada-118">The statements do not result in an error (the operations will return success), but have no effect.</span></span>  
  
 <span data-ttu-id="4bada-119">이 동작은 변경되지 않았지만 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터는 사용자에게 이 정보 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bada-119">This behavior has not changed, however beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this informational message alerts the user.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4bada-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="4bada-120">User Action</span></span>  
 <span data-ttu-id="4bada-121">별도의 동작이 필요 없지만, 로컬 또는 전역 임시 개체에 대해 감사 또는 권한을 설정하는 문을 제거해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="4bada-121">No action is necessary, but consider removing statements that attempt to set auditing or permissions on local or global temp objects.</span></span>  
  
  
