---
title: SQL Server Native Client 구성 속성(플래그 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 59af121d-c8b9-4faa-91a1-b664f2c9b441
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3ca7b87963fc3848bbb933a5c21f9d608d37d18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660219"
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a><span data-ttu-id="a036a-102">SQL Server Native Client 구성 속성(플래그 탭)</span><span class="sxs-lookup"><span data-stu-id="a036a-102">SQL Server Native Client Configuration Properties (Flags Tab)</span></span>
  <span data-ttu-id="a036a-103">이 머신의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 라이브러리 파일에서 제공하는 프로토콜을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서버와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients on this machine, communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers using the protocols provided in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client library file.</span></span> <span data-ttu-id="a036a-104">이 페이지에서 SSL(Secure Sockets Layer)을 사용하여 암호화된 연결을 요청하도록 클라이언트 컴퓨터를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-104">This page provides configures the client computer to request an encrypted connection using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="a036a-105">암호화된 연결을 설정할 수 없으면 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-105">If an encrypted connection cannot be established, the connection will fail.</span></span>  
  
 <span data-ttu-id="a036a-106">로그인 프로세스는 항상 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-106">The login process is always encrypted.</span></span> <span data-ttu-id="a036a-107">아래 옵션은 데이터 암호화에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-107">The options below apply only to encrypting data.</span></span> <span data-ttu-id="a036a-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 통신을 암호화하는 방법과 서버 인증서의 루트 인증 기관을 신뢰하도록 클라이언트를 구성하는 방법에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]온라인 설명서에서 " [!INCLUDE[ssDE](../../includes/ssde-md.md)] 연결 암호화" 및 "방법:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 암호화 연결 사용( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자)"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a036a-108">For more information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encrypts communication and for instructions on how to configure the client to trust the root authority of the server certificate, see "Encrypting Connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" and "How to: Enable Encrypted Connections to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a036a-109">옵션</span><span class="sxs-lookup"><span data-stu-id="a036a-109">Options</span></span>  
 <span data-ttu-id="a036a-110">**프로토콜 암호화 강제 사용**</span><span class="sxs-lookup"><span data-stu-id="a036a-110">**Force protocol encryption**</span></span>  
 <span data-ttu-id="a036a-111">SSL을 사용하여 연결을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-111">Request a connection using SSL.</span></span>  
  
 <span data-ttu-id="a036a-112">**서버 인증서 신뢰**</span><span class="sxs-lookup"><span data-stu-id="a036a-112">**Trust Server Certificate**</span></span>  
 <span data-ttu-id="a036a-113">**아니요**로 설정하면 클라이언트 프로세스에서 서버 인증서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-113">When set to **No**, the client process attempts to validate the server certificate.</span></span> <span data-ttu-id="a036a-114">클라이언트와 서버는 각각 공인 인증 기관에서 발급한 인증서를 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-114">The client and server must have each have a certificate issues from a public certification authority.</span></span> <span data-ttu-id="a036a-115">클라이언트 컴퓨터에 인증서가 없거나 인증서 유효성 검사에 실패하면 연결이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-115">If the certificate is not present on the client computer, or if the validation of the certificate fails, the connection is terminated.</span></span>  
  
 <span data-ttu-id="a036a-116">**예**로 설정하면 클라이언트가 서버 인증서의 유효성을 검사하지 않으므로 자체 서명된 인증서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-116">When set to **Yes**, the client does not validate the server certificate, thereby enabling the use of a self-signed certificate.</span></span>  
  
 <span data-ttu-id="a036a-117">**서버 인증서 신뢰** 는 **프로토콜 암호화 강제 사용** 이 **예**로 설정된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a036a-117">**Trust Server Certificate** is only available if **Force protocol encryption** is set to **Yes**.</span></span>  
  
  
