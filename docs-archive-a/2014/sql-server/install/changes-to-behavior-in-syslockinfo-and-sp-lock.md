---
title: Syslockinfo 및 sp_lock의 동작에 대 한 변경 내용 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65ace190004cab911dd8996642720620eba94935
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650517"
---
# <a name="changes-to-behavior-in-syslockinfo-and-sp_lock"></a><span data-ttu-id="b7f92-102">syslockinfo 및 sp_lock의 동작에 대한 변경입니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-102">Changes to behavior in syslockinfo and sp_lock</span></span>
  <span data-ttu-id="b7f92-103">**syslockinfo** 및 **sp_lock** 이 예기치 않은 값을 반환할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="b7f92-103">**syslockinfo** and **sp_lock** may return unexpected values.</span></span> <span data-ttu-id="b7f92-104">추가 행을 반환할 수도 있습니다. 반면에 이전 버전에서는 **syslockinfo** 및 **sp_lock** 이 잠금 리소스당 최대 두 개의 행을 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-104">They may also return additional rows, whereas previous versions of **syslockinfo** and **sp_lock** returned a maximum of two rows per lock resource.</span></span>  
  
 <span data-ttu-id="b7f92-105">**syslockinfo** 의 정보에 액세스하거나 **sp_lock** 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-105">To access information from **syslockinfo** or execute **sp_lock** requires VIEW SERVER STATE permission on the server.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b7f92-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b7f92-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b7f92-107">Description</span><span class="sxs-lookup"><span data-stu-id="b7f92-107">Description</span></span>  
 <span data-ttu-id="b7f92-108">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 **syslockinfo** 의 **rsc_objid** 및 **rsc_indid** 열과 **sp_lock** 의 **objid** 및 **indid** 열은 항상 개체 ID와 인덱스 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-108">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], the **rsc_objid** and **rsc_indid** columns in **syslockinfo** and the **objid** and **indid** columns in **sp_lock** consistently return the object ID and index ID.</span></span> <span data-ttu-id="b7f92-109">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서는 값 0이 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-109">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a value of 0 may be returned.</span></span>  
  
 <span data-ttu-id="b7f92-110">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 **syslockinfo** 및 **sp_lock** 은 단일 트랜잭션에서 지정한 잠금 리소스에 대해 최대 두 개의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-110">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **syslockinfo** and **sp_lock** return a maximum of two rows for any given lock resource in a single transaction.</span></span> <span data-ttu-id="b7f92-111">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터 잠금 분할을 사용할 경우 한 트랜잭션에서 실행 중인 동일한 리소스에 대해 여러 개의 행이 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-111">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], when lock partitioning is enabled, multiple rows for the same resource running under one transaction may be returned.</span></span> <span data-ttu-id="b7f92-112">최대 N + 1 개의 행이 반환 될 수 있습니다. 여기서 N은 Cpu의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-112">There may be up to N + 1 rows returned, where N is the number of CPUs.</span></span> <span data-ttu-id="b7f92-113">또한 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 가능하지 않았지만 이제는 동일한 리소스에 대해 GRANTED 및 WAITING 요청을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-113">Also, it is now possible to have GRANTED and WAITING requests displayed for the same resource, which was not possible in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="b7f92-114">사용 권한</span><span class="sxs-lookup"><span data-stu-id="b7f92-114">Permissions</span></span>  
 <span data-ttu-id="b7f92-115">을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f92-115">Requires VIEW SERVER STATE permission on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f92-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7f92-116">See Also</span></span>  
 <span data-ttu-id="b7f92-117">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b7f92-117">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b7f92-118">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="b7f92-118">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
