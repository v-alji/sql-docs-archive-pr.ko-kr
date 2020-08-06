---
title: 기본 추적 로그 파일 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fed8fb006427b4dda9d99c57cbabca8538efcad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649002"
---
# <a name="default-trace-log-files-disabled"></a><span data-ttu-id="1178e-102">기본 추적 로그 파일 해제</span><span class="sxs-lookup"><span data-stu-id="1178e-102">Default Trace Log Files Disabled</span></span>
  <span data-ttu-id="1178e-103">이 규칙은 sp_configure 저장 프로시저 기본 추적이 설정된 옵션의 값을 검사하여 기본 추적이 ON(1) 또는 OFF(0)로 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1178e-103">This rule checks the value of the sp_configure stored procedure default trace enabled option to determine whether default trace is set ON (1) or OFF (0).</span></span> <span data-ttu-id="1178e-104">이 옵션이 설정된 경우 기본 추적은 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에 대한 DDL 변경 사항 및 구성 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1178e-104">When this option is enabled, default tracing provides information about configuration and DDL changes to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="1178e-105">이러한 정보는 고객 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 고객 지원 서비스에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]관련 문제를 해결하는 데 도움이 되는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1178e-105">In some cases, this information can be helpful for customers and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support when they troubleshooting issues with the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="1178e-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="1178e-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="1178e-107">sp_configure 저장 프로시저를 사용하여 기본 추적 값을 1로 설정하여 추적을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1178e-107">Use the sp_configure stored procedure to enable tracing by setting the value of default trace enabled to 1.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="1178e-108">참조 항목</span><span class="sxs-lookup"><span data-stu-id="1178e-108">For More Information</span></span>  
 [<span data-ttu-id="1178e-109">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1178e-109">Server Configuration Options &#40;SQL Server&#41;</span></span>](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="1178e-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1178e-110">See Also</span></span>  
 [<span data-ttu-id="1178e-111">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="1178e-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
