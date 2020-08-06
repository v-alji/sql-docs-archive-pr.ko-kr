---
title: EKM provider enabled 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- external encryption provider
helpviewer_keywords:
- EKM provider enabled option
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b44e7f5e0801bb370a98abe79a6ea449c6f7409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741244"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a><span data-ttu-id="c22ca-102">EKM provider enabled 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="c22ca-102">EKM provider enabled Server Configuration Option</span></span>
  <span data-ttu-id="c22ca-103">`EKM provider enabled` 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 Extensible Key Management 디바이스 지원을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="c22ca-103">The `EKM provider enabled` option controls Extensible Key Management device support in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c22ca-104">기본적으로 이 옵션은 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c22ca-104">By default this option is off.</span></span>  
  
 <span data-ttu-id="c22ca-105">이 기능을 사용하거나 사용하지 않도록 설정하려면 다음 `sp_configure` 명령 중 하나를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="c22ca-105">To enable or disable the feature, issue one of the following `sp_configure` commands:</span></span>  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c22ca-106">이 옵션은 일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c22ca-106">This option is not enabled in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c22ca-107">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c22ca-107">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c22ca-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c22ca-108">See Also</span></span>  
 <span data-ttu-id="c22ca-109">[확장 가능 키 관리 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md) </span><span class="sxs-lookup"><span data-stu-id="c22ca-109">[Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md) </span></span>  
 <span data-ttu-id="c22ca-110">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c22ca-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="c22ca-111">[리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="c22ca-111">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="c22ca-112">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c22ca-112">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="c22ca-113">RECONFIGURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c22ca-113">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
