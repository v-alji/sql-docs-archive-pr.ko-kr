---
title: Ole Automation Procedures 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d34615ce1f808c1015c9c3d312a38a67dba291b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728683"
---
# <a name="ole-automation-procedures-server-configuration-option"></a><span data-ttu-id="e1e18-102">Ole Automation Procedures 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="e1e18-102">Ole Automation Procedures Server Configuration Option</span></span>
  <span data-ttu-id="e1e18-103">`Ole Automation Procedures` 옵션을 사용하여 OLE Automation 개체가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리 내에서 인스턴스화될 수 있는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-103">Use the `Ole Automation Procedures` option to specify whether OLE Automation objects can be instantiated within [!INCLUDE[tsql](../../includes/tsql-md.md)] batches.</span></span> <span data-ttu-id="e1e18-104">이 옵션은 정책 기반 관리 또는 **sp_configure** 저장 프로시저를 사용하여 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-104">This option can also be configured using the Policy-Based Management or the **sp_configure** stored procedure.</span></span> <span data-ttu-id="e1e18-105">자세한 내용은 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1e18-105">For more information, see [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).</span></span>  
  
 <span data-ttu-id="e1e18-106">`Ole Automation Procedures` 옵션을 다음 값으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-106">The `Ole Automation Procedures` option can be set to the following values.</span></span>  
  
 <span data-ttu-id="e1e18-107">0</span><span class="sxs-lookup"><span data-stu-id="e1e18-107">0</span></span>  
 <span data-ttu-id="e1e18-108">OLE Automation Procedures가 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-108">OLE Automation Procedures are disabled.</span></span> <span data-ttu-id="e1e18-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 새 인스턴스에 대한 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-109">Default for new instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e1e18-110">1</span><span class="sxs-lookup"><span data-stu-id="e1e18-110">1</span></span>  
 <span data-ttu-id="e1e18-111">OLE Automation Procedures가 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-111">OLE Automation Procedures are enabled.</span></span>  
  
 <span data-ttu-id="e1e18-112">OLE Automation Procedures가 설정되어 있는 경우 **sp_OACreate** 를 호출하면 OLE 공유 실행 환경이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-112">When OLE Automation Procedures are enabled, a call to **sp_OACreate** will start the OLE shared execution environment.</span></span>  
  
 <span data-ttu-id="e1e18-113">옵션의 현재 값은 `Ole Automation Procedures` **sp_configure** 시스템 저장 프로시저를 사용 하 여 보고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-113">The current value of the `Ole Automation Procedures` option can be viewed and changed by using the **sp_configure** system stored procedure.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e1e18-114">예제</span><span class="sxs-lookup"><span data-stu-id="e1e18-114">Examples</span></span>  
 <span data-ttu-id="e1e18-115">다음 예에서는 OLE Automation procedures의 현재 설정을 보는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-115">The following example shows how to view the current setting of OLE Automation procedures.</span></span>  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 <span data-ttu-id="e1e18-116">다음 예에서는 OLE Automation procedures를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1e18-116">The following example shows how to enable OLE Automation procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1e18-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1e18-117">See Also</span></span>  
 <span data-ttu-id="e1e18-118">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e1e18-118">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="e1e18-119">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e1e18-119">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="e1e18-120">[노출 영역 구성](../../relational-databases/security/surface-area-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e1e18-120">[Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) </span></span>  
 [<span data-ttu-id="e1e18-121">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e1e18-121">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
