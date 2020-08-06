---
title: 90 이상 호환성 모드에서 큼 상수는 크게 값 형식으로 입력 됩니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58acde8aaebdcac629463edcfb565eed13355ad4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646816"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a><span data-ttu-id="f201c-102">호환성 모드 90 이상에서 큰 상수는 큰 값 유형으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-102">Large constants are typed as large-value types in 90 or later compatibility modes</span></span>
  <span data-ttu-id="f201c-103">업그레이드 관리자가 큰 상수를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-103">Upgrade Advisor detected the presence of large constants.</span></span> <span data-ttu-id="f201c-104">크기가 8,000바이트 이상인 문자열 상수와 이진 상수는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 큰 개체 데이터 형식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-104">Character string constants and binary constants that are more than 8,000 bytes in size are treated as large object data types in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="f201c-105">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 큰 문자, 유니코드 및 이진 상수가 큰 값 유형으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, large character, Unicode, and binary constants, are typed as large-value types.</span></span>  
  
## <a name="component"></a><span data-ttu-id="f201c-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f201c-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="f201c-107">Description</span><span class="sxs-lookup"><span data-stu-id="f201c-107">Description</span></span>  
 <span data-ttu-id="f201c-108">CHARINDEX 및 PATINDEX와 같은 문자열 함수를 8,000바이트보다 큰 문자열 상수나 이진 상수와 함께 사용하면 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 에서는 오류 번호 8116이 반환되고 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 오류 번호 8152가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-108">When string functions, such as CHARINDEX and PATINDEX, are used with string or binary constants that exceed 8,000 bytes, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] returns error number 8116, and [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions return error number 8152.</span></span>  
  
 <span data-ttu-id="f201c-109">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 문자열 함수를 `text`, `ntext` 및 `image` 데이터 형식과 함께 사용하면 오류 번호 8116이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-109">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], the string functions return error 8116 when they are used with the `text`, `ntext`, and `image` data types.</span></span>  
  
 <span data-ttu-id="f201c-110">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 큰 상수가 각각 `varchar(max)`, `nvarchar(max)` 및 `varbinary(max)` 데이터 형식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-110">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, the large constants are treated as `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types, respectively.</span></span> <span data-ttu-id="f201c-111">이러한 데이터 형식은 문자열 함수와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-111">These data types are compatible with string functions.</span></span>  
  
 <span data-ttu-id="f201c-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 CHARINDEX 및 PATINDEX와 같은 문자열 함수가 검색할 문자 시퀀스가 포함된 문자열이 8,000바이트보다 작다고 간주하기 때문에</span><span class="sxs-lookup"><span data-stu-id="f201c-112">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, string functions, such as CHARINDEX and PATINDEX, assume the string that contains the sequence of characters to be found is less than 8,000 bytes.</span></span> <span data-ttu-id="f201c-113">CHARINDEX 및 PATINDEX에 대해 오류 번호 8152가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201c-113">This is why error 8152 is raised for CHARINDEX and PATINDEX.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f201c-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f201c-114">See Also</span></span>  
 <span data-ttu-id="f201c-115">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="f201c-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="f201c-116">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="f201c-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
