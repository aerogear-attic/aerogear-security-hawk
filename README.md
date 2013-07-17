# aerogear-security-hawk

## Getting started

### Dependencies

        <dependency>
             <groupId>org.jboss.aerogear</groupId>
             <artifactId>aerogear-security-hawk</artifactId>
             <version>0.1.0</version>
             <scope>compile</scope>
        </dependency>

### Project configuration

To provide more flexibility and enabling developers to easily implement their own server configuration if they choose to, a *HawkServer* producer must be provided. 

    import com.wealdtech.hawk.HawkServer;
    import com.wealdtech.hawk.HawkServerConfiguration;

    import javax.enterprise.inject.Produces;

    public class HawkConfigProducer {

        @Produces
        public HawkServer hawkConfig() {
            HawkServerConfiguration configuration = new HawkServerConfiguration.Builder().build();
            return new HawkServer.Builder().configuration(configuration).build();
        }
    }

AeroGear Security does not limit developers to choose any particular persistence provider. For this reason *HawkCredentialProvider* exists, you can easily integrate with persistence providers, LDAP servers, IDMs or whatever.

    import com.wealdtech.hawk.HawkCredentials;
    import org.jboss.aerogear.security.hawk.auth.HawkCredentialProvider;

    public class HawkCredentialsProvider implements HawkCredentialProvider {

        @Override
        public HawkCredentials findByKey(String key) {
            HawkCredentials credentials = new HawkCredentials.Builder()
                    .keyId("dh37fgj492je")
                    .key("werxhqb98rpaxn39848xrunpaw3489ruxnpa98w4rxn")
                    .algorithm(HawkCredentials.Algorithm.SHA256)
                    .build();
            return credentials;
        }
    }


## For further information see:

- [Hawk](https://github.com/hueniverse/hawk)
- [Hawk Java](https://github.com/wealdtech/hawk)

---
you can find a slightly better example at <https://github.com/aerogear/aerogear-controller-demo>



