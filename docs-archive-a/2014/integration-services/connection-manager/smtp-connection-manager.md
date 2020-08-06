---
title: SMTP 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f3c090ab672790901baae01ae86f8d22e008b4ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741188"
---
# <a name="smtp-connection-manager"></a><span data-ttu-id="b27dd-102">SMTP 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="b27dd-102">SMTP Connection Manager</span></span>
  <span data-ttu-id="b27dd-103">SMTP 연결 관리자를 사용하면 패키지에서 SMTP(Simple Mail Transfer Protocol) 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-103">An SMTP connection manager enables a package to connect to a Simple Mail Transfer Protocol (SMTP) server.</span></span> <span data-ttu-id="b27dd-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 메일 보내기 태스크에서는 SMTP 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-104">The Send Mail task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses an SMTP connection manager.</span></span>  
  
 <span data-ttu-id="b27dd-105">Microsoft Exchange를 SMTP 서버로 사용하는 경우 Windows 인증을 사용하려면 SMTP 연결 관리자를 구성해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-105">When using Microsoft Exchange as the SMTP server, you may need to configure the SMTP connection manager to use Windows Authentication.</span></span> <span data-ttu-id="b27dd-106">인증되지 않은 SMTP 연결을 허용하지 않도록 Exchange 서버를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-106">Exchange servers may be configured to not allow unauthenticated SMTP connections.</span></span>  
  
## <a name="configuration-the-smtp-connection-manager"></a><span data-ttu-id="b27dd-107">SMTP 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="b27dd-107">Configuration the SMTP Connection Manager</span></span>  
 <span data-ttu-id="b27dd-108">패키지에 SMTP 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 SMTP 연결로 확인되는 연결 관리자를 만들고, 연결 관리자 속성을 설정하고, 연결 관리자를 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-108">When you add an SMTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an SMTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="b27dd-109">연결 관리자의 `ConnectionManagerType` 속성이 `SMTP`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-109">The `ConnectionManagerType` property of the connection manager is set to `SMTP`.</span></span>  
  
 <span data-ttu-id="b27dd-110">다음과 같은 방법으로 SMTP 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-110">You can configure an SMTP connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="b27dd-111">연결 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-111">Provide a connection string.</span></span>  
  
-   <span data-ttu-id="b27dd-112">SMTP 서버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-112">Specify the name of an SMTP server.</span></span>  
  
-   <span data-ttu-id="b27dd-113">사용할 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-113">Specify the authentication method to use.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b27dd-114">SMTP 연결 관리자는 익명 인증과 Windows 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="b27dd-114">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="b27dd-115">기본 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-115">It does not support basic authentication.</span></span>  
  
-   <span data-ttu-id="b27dd-116">전자 메일 메시지를 보낼 때 SSL(Secure Sockets Layer)을 사용하여 통신을 암호화할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-116">Specify whether to encrypt communication using Secure Sockets Layer (SSL) when sending e-mail messages.</span></span>  
  
 <span data-ttu-id="b27dd-117">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-117">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b27dd-118">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [SMTP 연결 관리자 편집기](../smtp-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b27dd-118">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [SMTP Connection Manager Editor](../smtp-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="b27dd-119">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b27dd-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
