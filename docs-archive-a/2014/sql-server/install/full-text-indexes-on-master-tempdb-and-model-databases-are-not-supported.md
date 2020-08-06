---
title: Master, tempdb 및 model 데이터베이스에서는 전체 텍스트 인덱스가 지원 되지 않습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fbd5e3133ed87fed9bdaf6d668df62c6471df766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661510"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a><span data-ttu-id="d78c9-102">master, tempdb 및 model 데이터베이스에서는 전체 텍스트 인덱스가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d78c9-102">Full-text indexes on master, tempdb and model databases are not supported</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d78c9-103">에서는 시스템 데이터베이스에 전체 텍스트 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d78c9-103">does not allow full-text indexes on any system database.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d78c9-104">Description</span><span class="sxs-lookup"><span data-stu-id="d78c9-104">Description</span></span>  
 <span data-ttu-id="d78c9-105">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 전체 텍스트 인덱스가 master, tempdb 및 model 데이터베이스에서 지원되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d78c9-105">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], full-text indexes were supported on the master, tempdb, and model databases.</span></span>  
  
 <span data-ttu-id="d78c9-106">Master, tempdb 및 model 데이터베이스의 전체 텍스트 카탈로그는 업그레이드 하는 동안 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d78c9-106">Any full-text catalogs in the master, tempdb, and model databases are removed during the upgrade.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78c9-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d78c9-107">See Also</span></span>  
 [<span data-ttu-id="d78c9-108">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="d78c9-108">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
