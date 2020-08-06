---
title: SQL Server Reporting Services Standard 및 Enterprise의 CPU 및 메모리 제한에 대 한 변경 내용 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bd889344f5b0bc72320ff8467ebd6ecc654872f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648775"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a><span data-ttu-id="ff5c4-102">SQL Server Reporting Services Standard 및 Enterprise의 CPU 및 메모리 제한에 대한 변경입니다.</span><span class="sxs-lookup"><span data-stu-id="ff5c4-102">Changes to CPU and memory limits for SQL Server Reporting Services Standard and Enterprise</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="ff5c4-103">Reporting Services Standard 및 Enterprise에서는 최대 64GB의 시스템 메모리가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff5c4-103">Reporting Services Standard and Enterprise supports a maximum of 64 gigabytes of system memory.</span></span>  
  
## <a name="component"></a><span data-ttu-id="ff5c4-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ff5c4-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a><span data-ttu-id="ff5c4-105">Description</span><span class="sxs-lookup"><span data-stu-id="ff5c4-105">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ff5c4-106">Reporting Services Standard 및 Enterprise에서는 최대 64GB의 시스템 메모리가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff5c4-106">Reporting Services Standard and Enterprise supports a maximum of 64 gigabytes of system memory.</span></span> <span data-ttu-id="ff5c4-107">새로운 제한 사항에 맞게 현재 시스템 설정을 다시 구성해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5c4-107">You may need to reconfigure your current system settings to align with the new limits.</span></span>  
  
 <span data-ttu-id="ff5c4-108">다른 버전의 CPU 및 메모리 제한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 버전별 계산 용량 제한](../compute-capacity-limits-by-edition-of-sql-server.md)및 [SQL Server 버전에서 지 원하는 메모리](https://go.microsoft.com/fwlink/?LinkId=212633)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff5c4-108">For more information about CPU and memory limits for other editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md), and [Memory Supported by the Editions of SQL Server](https://go.microsoft.com/fwlink/?LinkId=212633).</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ff5c4-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="ff5c4-109">Corrective Action</span></span>  
 <span data-ttu-id="ff5c4-110">새로운 CPU 및 메모리 제한 사항에 맞게 현재 시스템 설정을 다시 구성해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff5c4-110">You may need to reconfigure your current system settings to align with the new CPU and memory limits.</span></span> <span data-ttu-id="ff5c4-111">자세한 내용은 [ALTER SERVER configuration &#40;transact-sql&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)및 [서버 메모리 서버 구성 옵션](../../database-engine/configure-windows/server-memory-server-configuration-options.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff5c4-111">For more information, see [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql), and [Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5c4-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff5c4-112">See Also</span></span>  
 <span data-ttu-id="ff5c4-113">[SQL Server 2014 버전에서 지 원하는 기능](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="ff5c4-113">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 [<span data-ttu-id="ff5c4-114">이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="ff5c4-114">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
