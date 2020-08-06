---
title: SMO 개체 모델 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: stevestein
ms.author: sstein
ms.openlocfilehash: c973e381a6cc7de44a0072d012147271eaa609ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728180"
---
# <a name="smo-object-model"></a><span data-ttu-id="603b9-102">SMO 개체 모델</span><span class="sxs-lookup"><span data-stu-id="603b9-102">SMO Object Model</span></span>
  <span data-ttu-id="603b9-103">SMO 개체 모델은 개체의 계층으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="603b9-103">The SMO object model is made up of a hierarchy of objects.</span></span> <span data-ttu-id="603b9-104"><xref:Microsoft.SqlServer.Management.Smo.Server> 개체가 최상위 개체이고 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체 아래에 모든 인스턴스 클래스 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="603b9-104">The <xref:Microsoft.SqlServer.Management.Smo.Server> object is the top level object and all instance class objects reside under the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span>  
  
 <span data-ttu-id="603b9-105"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 클래스는 별도의 개체 계층을 포함하는 최상위 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="603b9-105">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> class is a top level class with a separate object hierarchy.</span></span> <span data-ttu-id="603b9-106"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>개체는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 공급자를 통해 사용할 수 있는 서비스 및 네트워크 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="603b9-106">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object represents [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings available through the WMI Provider.</span></span>  
  
 <span data-ttu-id="603b9-107"><xref:Microsoft.SqlServer.Management.Smo.Server> 및 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 개체 외에도 태스크나 작업을 나타내는 <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> 또는 <xref:Microsoft.SqlServer.Management.Smo.Restore>와 같은 여러 가지 유틸리티 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="603b9-107">Besides the <xref:Microsoft.SqlServer.Management.Smo.Server> and <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> objects, there are several utility classes that represent tasks or operations, such as <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup>, or <xref:Microsoft.SqlServer.Management.Smo.Restore></span></span>  
  
 <span data-ttu-id="603b9-108">SMO 개체 모델은 여러 개의 네임스페이스로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="603b9-108">The SMO object model is made up of several namespaces.</span></span> <span data-ttu-id="603b9-109">자세한 내용은 [SMO 네임 스페이스](smo-object-model-namespaces.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="603b9-109">For more information, see [SMO Namespaces](smo-object-model-namespaces.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603b9-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="603b9-110">See Also</span></span>  
 <span data-ttu-id="603b9-111">[SMO 개체 모델 다이어그램](smo-object-model-diagram.md) </span><span class="sxs-lookup"><span data-stu-id="603b9-111">[SMO Object Model Diagram](smo-object-model-diagram.md) </span></span>  
 <span data-ttu-id="603b9-112">[SMO 네임 스페이스](smo-object-model-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="603b9-112">[SMO Namespaces](smo-object-model-namespaces.md) </span></span>  
 [<span data-ttu-id="603b9-113">구성 관리용 WMI 공급자 개념</span><span class="sxs-lookup"><span data-stu-id="603b9-113">WMI Provider for Configuration Management Concepts</span></span>](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
