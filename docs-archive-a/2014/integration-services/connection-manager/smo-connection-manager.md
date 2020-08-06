---
title: SMO 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 988eef214608399bc3ec483d9976c2f5d52acb2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741191"
---
# <a name="smo-connection-manager"></a><span data-ttu-id="00f23-102">SMO 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="00f23-102">SMO Connection Manager</span></span>
  <span data-ttu-id="00f23-103">SMO 연결 관리자를 사용하면 패키지에서 SMO(SQL Management Objects) 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-103">An SMO connection manager enables a package to connect to a SQL Management Object (SMO) server.</span></span> <span data-ttu-id="00f23-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 전송 태스크에서는 SMO 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-104">The transfer tasks that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes use an SMO connection manager.</span></span> <span data-ttu-id="00f23-105">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 전송하는 전송 로그인 태스크에서는 SMO 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-105">For example, the Transfer Logins task that transfers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins uses an SMO connection manager.</span></span>  
  
 <span data-ttu-id="00f23-106">패키지에 SMO 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 SMO 연결로 확인되는 연결 관리자를 만들고, 연결 관리자 속성을 설정하고, 연결 관리자를 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-106">When you add an SMO connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an SMO connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="00f23-107">연결 관리자의 `ConnectionManagerType` 속성이 `SMOServer`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-107">The `ConnectionManagerType` property of the connection manager is set to `SMOServer`.</span></span>  
  
 <span data-ttu-id="00f23-108">다음과 같은 방법으로 SMO 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-108">You can configure an SMO connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="00f23-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 설치된 서버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-109">Specify the name of a server on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
-   <span data-ttu-id="00f23-110">서버에 연결하기 위한 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-110">Select the authentication mode for connecting to the server.</span></span>  
  
## <a name="configuration-of-the-smo-connection-manager"></a><span data-ttu-id="00f23-111">SMO 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="00f23-111">Configuration of the SMO Connection Manager</span></span>  
 <span data-ttu-id="00f23-112">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="00f23-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [SMO 연결 관리자 편집기](../smo-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f23-113">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [SMO Connection Manager Editor](../smo-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="00f23-114">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f23-114">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f23-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00f23-115">See Also</span></span>  
 [<span data-ttu-id="00f23-116">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="00f23-116">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
