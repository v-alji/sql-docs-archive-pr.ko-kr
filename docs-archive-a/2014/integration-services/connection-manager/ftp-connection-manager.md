---
title: FTP 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a402f399ba4b7e69fc1d3cbca9dd64b32217ced1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729719"
---
# <a name="ftp-connection-manager"></a><span data-ttu-id="28fe1-102">FTP 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="28fe1-102">FTP Connection Manager</span></span>
  <span data-ttu-id="28fe1-103">FTP 연결 관리자를 사용하면 패키지에서 FTP(파일 전송 프로토콜) 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-103">An FTP connection manager enables a package to connect to a File Transfer Protocol (FTP) server.</span></span> <span data-ttu-id="28fe1-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 FTP 태스크에서는 이 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-104">The FTP task that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager.</span></span>  
  
 <span data-ttu-id="28fe1-105">패키지에 FTP 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 FTP 연결로 확인되는 연결 관리자를 만들고, 연결 관리자 속성을 설정하고, 연결 관리자를 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-105">When you add an FTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that can be resolved as an FTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="28fe1-106">연결 관리자의 `ConnectionManagerType` 속성이 `FTP`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-106">The `ConnectionManagerType` property of the connection manager is set to `FTP`.</span></span>  
  
 <span data-ttu-id="28fe1-107">다음과 같은 방법으로 FTP 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-107">You can configure the FTP connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="28fe1-108">서버 이름과 서버 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-108">Specify a server name and server port.</span></span>  
  
-   <span data-ttu-id="28fe1-109">익명 액세스를 지정하거나 기본 인증을 위한 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-109">Specify anonymous access, or provide a user name and a password for basic authentication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="28fe1-110">FTP 연결 관리자는 익명 인증과 기본 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="28fe1-110">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="28fe1-111">Windows 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-111">It does not support Windows Authentication.</span></span>  
  
-   <span data-ttu-id="28fe1-112">제한 시간, 다시 시도 횟수 및 한 번에 복사할 데이터 양을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-112">Set the time-out, number of retries, and the amount of data to copy at a time.</span></span>  
  
-   <span data-ttu-id="28fe1-113">FTP 연결 관리자에서 Passive 또는 Active 모드를 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-113">Indicate whether the FTP connection manager uses passive or active mode.</span></span>  
  
 <span data-ttu-id="28fe1-114">FTP 연결 관리자에서 연결하는 FTP 사이트의 구성에 따라 연결 관리자의 다음 기본값을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-114">Depending on the configuration of the FTP site to which the FTP connection manager connects, you may need to change the following default values of the connection manager:</span></span>  
  
-   <span data-ttu-id="28fe1-115">서버 포트는 21로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-115">The server port is set to 21.</span></span> <span data-ttu-id="28fe1-116">FTP사이트에서 수신하는 포트를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-116">You should specify the port that the FTP site listens to.</span></span>  
  
-   <span data-ttu-id="28fe1-117">사용자 이름은 "anonymous"로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-117">The user name is set to "anonymous".</span></span> <span data-ttu-id="28fe1-118">FTP 사이트에 필요한 자격 증명을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-118">You should provide the credentials that the FTP site requires.</span></span>  
  
## <a name="activepassive-modes"></a><span data-ttu-id="28fe1-119">Active/Passive 모드</span><span class="sxs-lookup"><span data-stu-id="28fe1-119">Active/Passive Modes</span></span>  
 <span data-ttu-id="28fe1-120">FTP 연결 관리자는 Active 모드 또는 Passive 모드를 사용하여 파일을 보내고 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-120">An FTP connection manager can send and receive files using either active mode or passive mode.</span></span> <span data-ttu-id="28fe1-121">Active 모드에서는 서버가 데이터 연결을 시작하고, Passive 모드에서는 클라이언트가 데이터 연결을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-121">In active mode, the server initiates the data connection, and in passive mode, the client initiates the data connection.</span></span>  
  
## <a name="configuration-of-the-ftp-connection-manager"></a><span data-ttu-id="28fe1-122">FTP 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="28fe1-122">Configuration of the FTP Connection Manager</span></span>  
 <span data-ttu-id="28fe1-123">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-123">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="28fe1-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [FTP 연결 관리자 편집기](../ftp-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="28fe1-124">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [FTP Connection Manager Editor](../ftp-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="28fe1-125">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="28fe1-125">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28fe1-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28fe1-126">See Also</span></span>  
 <span data-ttu-id="28fe1-127">[FTP 태스크](../control-flow/ftp-task.md) </span><span class="sxs-lookup"><span data-stu-id="28fe1-127">[FTP Task](../control-flow/ftp-task.md) </span></span>  
 [<span data-ttu-id="28fe1-128">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="28fe1-128">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
