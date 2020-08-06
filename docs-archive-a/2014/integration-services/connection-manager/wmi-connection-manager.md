---
title: WMI 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f15aefb0ed112f1d5b7bb05421750b6689a11339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651859"
---
# <a name="wmi-connection-manager"></a><span data-ttu-id="6f051-102">WMI 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="6f051-102">WMI Connection Manager</span></span>
  <span data-ttu-id="6f051-103">WMI 연결 관리자를 사용하면 패키지에서 WMI(Windows Management Instrumentation)를 사용하여 엔터프라이즈 환경의 정보를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-103">A WMI connection manager enables a package to use Windows Management Instrumentation (WMI) to manage information in an enterprise environment.</span></span> <span data-ttu-id="6f051-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 웹 서비스 태스크에서는 WMI 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-104">The Web Service task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses a WMI connection manager.</span></span>  
  
 <span data-ttu-id="6f051-105">패키지에 WMI 연결 관리자를 추가 하면에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임에 wmi 연결로 확인 되는 연결 관리자를 만들고, 연결 관리자 속성을 설정 하 고, 연결 관리자를 `Connections` 패키지의 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-105">When you add a WMI connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a WMI connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="6f051-106">연결 관리자의 `ConnectionManagerType` 속성이 `WMI`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-106">The `ConnectionManagerType` property of the connection manager is set to `WMI`.</span></span>  
  
## <a name="configuration-of-the-wmi-connection-manager"></a><span data-ttu-id="6f051-107">WMI 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="6f051-107">Configuration of the WMI Connection Manager</span></span>  
 <span data-ttu-id="6f051-108">다음과 같은 방법으로 WMI 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-108">You can configure a WMI connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="6f051-109">서버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-109">Specify the name of a server.</span></span>  
  
-   <span data-ttu-id="6f051-110">서버에 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-110">Specify a namespace on the server.</span></span>  
  
-   <span data-ttu-id="6f051-111">서버에 연결하기 위한 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-111">Select the authentication mode for connecting to the server.</span></span>  
  
 <span data-ttu-id="6f051-112">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="6f051-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [WMI 연결 관리자 편집기](../wmi-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f051-113">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [WMI Connection Manager Editor](../wmi-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="6f051-114">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f051-114">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f051-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f051-115">See Also</span></span>  
 <span data-ttu-id="6f051-116">[웹 서비스 태스크](../control-flow/web-service-task.md) </span><span class="sxs-lookup"><span data-stu-id="6f051-116">[Web Service Task](../control-flow/web-service-task.md) </span></span>  
 [<span data-ttu-id="6f051-117">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="6f051-117">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
